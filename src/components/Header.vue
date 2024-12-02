<script>
export default {
  props: {
    searchQuery: String,
    onSearch: Function
  },
  data() {
    return {
      localSearchQuery: this.searchQuery
    };
  },
  methods: {
    handleInput(event) {
      this.localSearchQuery = event.target.value;
    },
    handleSubmit(event) {
      event.preventDefault();
      this.onSearch(this.localSearchQuery);
    }
  }
}
</script>

<template>
  <header>
    <nav>
        <ul>
            <li>
                <a href="#">Каталог</a>
            </li>
            <li>
                <a href="#">Доставка</a>
            </li>
            <li>
                <a href="#">Оплата</a>
            </li>
            <li>
                <a href="#">Контакты</a>
            </li>
            <li>
                <a href="#">О компании</a>
            </li>
        </ul>
    </nav>
    <form @submit="handleSubmit">
        <input 
          type="text" 
          :value="localSearchQuery" 
          @input="handleInput" 
          placeholder="Поиск по названию картины"
        >
      <button type="submit">Найти</button>
    </form>
  </header>
</template>

<style scoped>
header {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
    height: 97px;
    border: 1px solid #e1e1e1;

    @media (max-width: 1240px) {
        flex-direction: column;
        justify-content: space-around;
    }
}

nav {
    width: 632px;
    display: flex;
    justify-content: flex-end;

    @media (max-width: 1240px) {
        justify-content: center;
        width: 100%;
    }
}

ul {
    display: flex;
    padding: 0;
    margin: 0;

    @media (max-width: 550px) {
        width: 100%;
        justify-content: space-between;
    }
}

li {
    list-style-type: none;
    width: 107px;

    @media (max-width: 1240px) {
        display: flex;
        justify-content: center;
    }

    @media (max-width: 550px) {
        width: fit-content;
    }
}

a {
    text-decoration: none;
    font-family: Merriweather;
    font-size: 14px;
    font-weight: 400;
    line-height: 21px;
    color: #343030;

    @media (max-width: 400px) {
            font-size: 12px; 
        }
}

form {
    margin-left: 147px;

    @media (max-width: 1240px) {
        margin: 0;
    }
}

input {
    width: 294px;
    height: 46px;
    border: 1px solid #e1e1e1;
    padding-left: 16px;
    font-family: Merriweather;
    font-size: 14px;
    font-weight: 400;
    line-height: 21px;
    color: #9f9f9f;

    @media (max-width: 550px) {
        height: 28px;
        width: 228px;
    }
}

button {
    border: 0;
    padding: 0;
    width: 122px;
    height: 48px;
    background-color: #403432;
    color: #fff;
    font-family: Merriweater;
    font-weight: 700;
    font-size: 14px;
    line-height: 21px;

    @media (max-width: 550px) {
        height: 32px;
        width: 78px;
    }
}
</style>