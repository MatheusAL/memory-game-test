<template>
    <div class="game-board">
      <h1 class="game-title d-flex justify-content-center">Memory Game</h1>
      <!-- Game board content here -->
      <div class="game-board-grid container mt-5 pt-3 pb-3 px-3">
        <card v-for="card in shuffledCards" :card="card" :key="card.id" @flippedCard="flipCard"/>
      </div>
      <div class="game-info d-flex container mt-3 justify-content-between">
        <h1 class="game-movements">Number of movements: {{ numberOfMoves }} </h1>
        <reset-button />
      </div>
    </div>
</template>
  
<script>
import Card from "./Card.vue"
import ResetButton from "./ResetButton.vue"
export default {
  name: 'GameBoard',
  components: { Card, ResetButton },
  data() {
    return {
      /* Game board data here */
      cards: [
        {
          id: 1,
          image: '',
          isVisible: false,
          name: 'Card 1',
          isFound: false,
        },
        {
          id: 2,
          image: '',
          isVisible: false,
          name: 'Card 2',
          isFound: false,
        },
        {
          id: 3,
          image: '',
          isVisible: false,
          name: 'Card 3',
          isFound: false,
        },
        {
          id: 4,
          image: '',
          isVisible: false,
          name: 'Card 4',
          isFound: false,
        },
        {
          id: 5,
          image: '',
          isVisible: false,
          name: 'Card 5',
          isFound: false,
        },
        {
          id: 6,
          image: '',
          isVisible: false,
          name: 'Card 6',
          isFound: false,
        },
        {
          id: 7,
          image: '',
          isVisible: false,
          name: 'Card 7',
          isFound: false,
        },
        {
          id: 8,
          image: '',
          isVisible: false,
          name: 'Card 8',
          isFound: false,
        },
        {
          id: 9,
          image: '',
          isVisible: false,
          name: 'Card 9',
          isFound: false,
        },
        {
          id: 10,
          image: '',
          isVisible: false,
          name: 'Card 10',
          isFound: false,
        }
      ],
      duplicatedCards: [],
      numberOfMoves: 0,
      cardsFlipped: 0
    };
  },
  created () {
    const cards1 = [...this.cards];
    const cards2 = [...this.cards];
    //const cards3 = structuredClone(cards2);
    const emptyArray = [];
    const lastIndex = cards1[cards1.length-1].id;
    cards2.forEach((card) => {
      card.id = card.id + lastIndex;
    });
    this.duplicatedCards = emptyArray.concat(cards1, cards2);
  },
  watch: {
    cardsFlipped () {
      if (this.cardsFlipped === 2) {
        this.verifyMovement();
      }
    }
  },
  computed: {
    shuffledCards () {
      return this.duplicatedCards.sort(() => Math.random() - 0.5);
    }
  },
  methods: {
    /* Game board methods here */
    flipCard(id) {
      const foundCard = this.shuffledCards.find((card)=> card.id === id);
      if (foundCard) {
        if (foundCard.isVisible) {
          this.cardsFlipped = this.cardsFlipped - 1;  
        } else {
          this.cardsFlipped = this.cardsFlipped + 1;
        } 
        foundCard.isVisible = !foundCard.isVisible;
      }
    },
    verifyMovement () {
      this.numberOfMoves = this.numberOfMoves + 1;
      if (this.card1 === this.card2) {
        console.log('found');
      }
      // Reset all cards that are not found
      setTimeout(() => {
        this.shuffledCards = this.shuffledCards.map((card) => {
          if (!card.isFound) {
            card.isVisible = false
          }
        });
      }, "750");
      this.cardsFlipped = 0;
    }
  },
};
</script>

<style scoped>
  .game-board {
    background-color: black;
    height: 100vh;
    width: 100vw;
  }
  .game-title {
    color:#38c986;
  }

  .game-board-grid {
    background-color: #fff;
    display: grid;
    grid-template-columns: repeat(5, 1fr);
    grid-auto-rows: 150px;
    gap: 20px;
  }
  .game-movements {
    color:#38c986;
  }
</style>
