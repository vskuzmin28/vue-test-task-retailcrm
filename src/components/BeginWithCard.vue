<template lang='pug'>
    .card
        .container
            .row
                .col-md-12
                    h3.card__title Путешествие мечты начинается с CARD PLUS
                    p.card__desc Мы продумали каждую мелочь. Владельцы CARD PLUS получают особый пакет привилегий, необходимый для любого путешествия
            
            ul.card__list.row
                li.card__list-item.col-lg-6.col-xl-3.col-md-6(v-for="ticketservice in ticketservices" :key="ticketservice.id")
                    img.card__list-icon(:src="ticketservice.img" alt="@@")
                    p.card__list-title {{ ticketservice.title }}
                    span.card__list-desc {{ ticketservice.description }}
</template>

<script>
export default {
    data() {
        return {
            ticketservices: [
                {id: 0, title:'Билеты любых авиакомпаний', description: 'Предложения от 300+ авиакомпаний, 185+ lowcost перевозчиков, чартеры от 60 крупных российскихтуроператоров', img: '/img/icons/icon-1.svg'},
                {id: 1, title:'Мили больше не сгорают', description: 'Мили, накопленные при оплате картой AlfaTravel, не сгорают и остаются на вашем счете, пока вы не решите их потратить', img: '/img/icons/icon-2.svg'},
                {id: 2, title:'Продвинутая страховка – бесплатно', description: 'Расширенная страховка для всей семьи с учетом экстремальных видов спорта и алкоголя', img: '/img/icons/icon-3.svg'},
                {id: 3, title:'Доступ к счетам в разных валютах', description: 'Текущие счета в рублях, долларах США, евро, английских фунтах стерлингов и швейцарских франках открываются в любой момент', img: '/img/icons/icon-4.svg'}
            ]
        }
    }
}
</script>

<style lang="scss" scoped>
    @import '@/assets/styles/main.scss';
    
    .card {

        &__title {
            margin: 0 0 10px 20px;
            font-family: Geometria;
            font-size: 30px;
            line-height: 38px;
            letter-spacing: 0.2px;
            text-align: center;
            color: $white;

            @media screen and (max-width: 425px) {
                margin-left: 0;
                font-size: 22px;
                line-height: 26px;
                margin-bottom: 40px;
            }

        }

        &__desc {
            padding: 0 26%;
            margin: 0 0 0 8px;
            width: 100%;
            font-family: Geometria;
            font-size: 14px;
            line-height: 18px;
            letter-spacing: 0.2px;
            text-align: center;
            color: $gray;

            @media screen and (max-width: $tablet) {
                padding: 0 12%;
            }

        }

        &__list {
            margin-top: 86px;
            padding: 0 7%;
            list-style: none;

            @media screen and (max-width: 1024px) {
                padding: 0 6%;
            }

            @media screen and (max-width: $tablet) {
                margin-top: 44px;
            }

            &-item {
                padding-right: 50px;
                margin-right: 20px;

                @media screen and (max-width: 1024px) {
                    padding: 0;
                    margin: 0;
                    margin-bottom: 30px;
                }

                @media screen and (max-width: $tablet) {
                    padding-right: 60px;
                    margin-right: 0px;
                }

                @media screen and (max-width: 425px) {
                    text-align: center;
                    margin-right: 0;
                    padding-right: 0;
                    padding-left: 0;
                }

                &:nth-child(even) {
                    @media screen and (max-width: $tablet) {
                        padding-left: 26px;
                    }

                    @media screen and (max-width: 425px) {
                        padding-left: 0px;
                    }

                }

                &:nth-child(2) {
                    .block-begin-with-card__list-icon {
                        margin-bottom: 19px;
                    }
                }

                &:last-child {
                    margin-right: -60px !important;
                    padding-right: 0;

                    @media screen and (max-width: $tablet) {
                        margin: 0;
                        padding-right: 60px;
                    }

                    @media screen and (max-width: 425px) {
                        padding-right: 0;
                        padding-left: 0;
                    }

                }

            }

            &-icon {
                margin-bottom: 23px;
                margin-left: -10px;

                @media screen and (max-width: 425px) {
                    margin-left: 0;
                }

            }

            &-title {
                margin: -5px 0 8px -2px;
                width: 80%;
                font-family: Geometria;
                font-weight: bold;
                font-size: 18px;
                line-height: 23px;
                color: $white;

                @media screen and (max-width: 425px) {
                    width: 100%;
                    margin-left: 0;
                }

            }

            &-desc {
                width: 100%;
                margin: 0;
                padding: 0;
                font-family: Geometria;
                font-style: normal;
                font-weight: bold;
                font-size: 14px;
                line-height: 20px;
                color: $gray;
            }

        }

    }
</style>