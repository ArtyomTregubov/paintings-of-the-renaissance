<script>
export default {
  props: {
    card: {
      type: Object,
      required: true
    }
  },
  methods: {
    closePopup() {
      this.$emit('close');
    }
  }
}
</script>

<template>
    <section className="popup">
        <div className="container">
            <div className="button-container">
                <button @click="closePopup">Х</button>
            </div>
            <img :src="card.image" alt="Картина" />
            <span className="description">{{ card.description }}</span>
            <span className="price">{{ card.price }}</span>
        </div>
    </section>
</template>

<style scoped>
    .popup {
        display: block;
        width: 500px;
        position: fixed;
        z-index: 1;
        top: 82px;
        background-color: #d9d9d9;
        overflow-x: hidden;
        transition: 0.5s;
        opacity: 0.93;

        @media (max-width: 600px) {
            width: 320px; 
        }
    }

    .container {
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    .button-container {
        display: flex;
        flex-direction: row-reverse;
        width: 100%;
    }

    button {
        border: 0;
        padding: 0;
        width: 37px;
        height: 33px;
        background-color: transparent;
        font-size: 17px;
        font-family: cursive;
        color: #693b7b;
    }

    img {
        width: 440px;
        margin-bottom: 29px;

        @media (max-width: 600px) {
            width: 80%; 
        }
    }

    .description {
        margin: 0 33px 33px;
        font-family: Merriweather;
        font-size: 13px;
    }

    .price {
        display: flex;
        width: 90%;
        margin: 0 0 33px 33px;
        font-family: Merriweather;
    }
</style>