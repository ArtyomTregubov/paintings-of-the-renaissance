<script>
import Popup from './Popup.vue';

export default {
  components: { Popup },
  props: {
    cards: {
      type: Array,
      required: true
    },
    searchQuery: {
      type: String,
      default: ''
    }
  },
  data() {
    return {
      cartStatus: this.loadCartStatus(),
      isPopupVisible: false,
      selectedCard: null
    };
  },
  computed: {
    filteredCards() {
      return this.searchQuery 
        ? this.cards.filter(card => card.title.toLowerCase().includes(this.searchQuery.toLowerCase()))
        : this.cards;
    }
  },
  methods: {
    loadCartStatus() {
      const savedStatus = localStorage.getItem('cartStatus');
      return savedStatus ? JSON.parse(savedStatus) : {};
    },
    saveCartStatus() {
      localStorage.setItem('cartStatus', JSON.stringify(this.cartStatus));
    },
    handleBuy(cardId) {
      this.cartStatus[cardId] = 'обработка';
      this.saveCartStatus();
      setTimeout(() => {
        this.cartStatus[cardId] = 'в корзине';
        this.saveCartStatus();
      }, 2000);
    },
    openPopup(card) {
      this.selectedCard = card;
      this.isPopupVisible = true;
    },
    closePopup() {
      this.isPopupVisible = false;
    }
  }
}
</script>

<template>
    <main>
      <h2>Картины эпохи возрождения</h2>
      <section>
        <article v-for="card in filteredCards" :key="card.id" :class="{ 'sold-out': card.price === 'Продана на аукционе' }">
            <img :src="card.image" alt="{{ card.alt }}" @click="openPopup(card)">
            <h3>{{card.title}}</h3>
            <h3>{{card.artist}}</h3>
            <div className="container">
                <div className="prices">
                    <span>{{ card.discount }}</span>
                    <h4>{{card.price}}</h4>
                </div>
                <button v-if="card.price !== 'Продана на аукционе'" @click="handleBuy(card.id)">
                  {{ cartStatus[card.id] || 'Купить' }}
                </button>
            </div>
        </article>
      </section>
    </main>

    <Popup v-if="isPopupVisible" @close="closePopup" :card="selectedCard"/>
    
</template>

<style scoped>
    main {
      display: flex;
      flex-direction: column;
      width: 1216px;
      min-height: 733px;

      @media (max-width: 1216px) {
        width: 100%;
    }
  }

  h2 {
    margin: 45px 0 39px;
    font-family: Merriweather;
    font-size: 24px;
    font-weight: 700;
    line-height: 36px;
    color: #343030;

    @media (max-width: 1216px) {
      display: flex;
      justify-content: center;
    }

    @media (max-width: 400px) {
      font-size: 20px;
    }
  }

  section {
    width: 100%;
    display: grid;
    justify-items: center;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 32px;
  }

  article {
    border: 1px solid #e1e1e1;
    width: 280px;
  }

  img {
    width: 280px;
    height: 160px;
    margin-bottom: 20px;
  }

  h3 {
    margin: 0 0 0 24px;
    font-family: Merriweather;
    font-weight: 400;
    font-size: 18px;
    line-height: 27px;
    color: #343030;
  }

  .container {
    display: flex;
    justify-content:space-between ;
    width: 232px;
    margin: 22px 0 24px 26px;
  }

  .prices {
    display: flex;
    flex-direction: column;
    justify-content: center;
  }

  span {
    font-family: Merriweather;
    font-size: 14px;
    font-weight: 300;
    line-height: 21px;
    text-decoration: line-through;
    color: #a0a0a0
  }

  h4 {
    margin: 0;
    font-family: Merriweather;
    font-size: 16px;
    font-weight: 700;
    line-height: 24px;
    color: #343030;
  }

  button {
    border: 0;
    padding: 0;
    width: 118px;
    height: 48px;
    background-color: #382e2b;
    font-family: Merriweather;
    font-size: 14px;
    font-weight: 700;
    line-height: 21px;
    color: #f4f6f9
      }

  .sold-out {
    opacity: 0.5; /* Затенение карточки */
    pointer-events: none; /* Отключение взаимодействия */
  }
</style>