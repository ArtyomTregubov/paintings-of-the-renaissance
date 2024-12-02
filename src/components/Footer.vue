<script>
export default {

}
</script>

<template>
    <footer>
        <div className="box">
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
            <div className="container">
                <article>
                    <img src="/images/phone_icon.png" alt="Иконка телефона"/>
                    <span>+7(812)555-55-55</span>
                </article>
                <article>
                    <img src="/images/adress_icon.png" alt="Иконка адреса"/>
                    <span>г. Санкт-Петербург, ул. Ефимова, 3</span>
                </article>
            </div>
        </div>
    </footer>
</template>

<style scoped>
    footer {
        display: flex;
        justify-content: center;
        align-items: center;
        width: 100%;
        height: 97px;
        background-color: #eceaea;
        margin-top: 33px;
    }

    .box {
        display: flex;
        justify-content: flex-end;
        width: 69%;

        @media (max-width: 1710px) {
            flex-direction: column;
            align-items: center;
            width: 100%;
        }
    }

    nav {
        margin-right: 126px;

        @media (max-width: 1710px) {
            margin: 0;

        }

        @media (max-width: 590px) {
            width: 100%;
            
        }
    }

    ul {
        width: 545px;
        display: flex;
        justify-content: space-between;
        padding: 0;
        margin: 0;

        @media (max-width: 590px) {
            width: 100%;
            justify-content: space-around;
            
        }
    }

    li {
        list-style-type: none;
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

    .container {
        display: flex;
        justify-content: space-between;
        width: 38%;
        height: 22px;

        @media (max-width: 1710px) {
            flex-direction: column;
            align-items: center;
            width: 100%;
        }
    }

    article {
        display: flex;
        align-items: center;

    }

    img {
        height: 14px;
        margin-right: 8px;
    }

    span {
        font-family: Merriweather;
        font-size: 14px;
        font-weight: 400;
        line-height: 21px;

        @media (max-width: 400px) {
            font-size: 12px; 
        }
    }
</style>