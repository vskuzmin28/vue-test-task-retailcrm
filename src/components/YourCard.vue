<template lang='pug'>
    .your-card
        .container
            .row
                .col-lg-10.col-md-12
                    h2.your-card__title 
                        | Твоя премиум карта
                        span.your-card__desc Лучшая карта для любителей путешествий
            .row
                .col-lg-5.col-md-12
                    ul.your-card__list
                        li.your-card__list-item(v-for="cardlist in cardlists" :key="cardlist.id")
                            p.your-card__list-title {{ cardlist.value }}
                            span.your-card__list-desc {{ cardlist.description }}
            .your-card__button.button(v-on:click="isPopupVisible = !isPopupVisible" title="") Заказать сейчас

            img.your-card__card(
                src="./../assets/img/card.png" alt="@@"
                v-if="onClickBurger"
                v-bind:class="{'your-card__card_active' : burgerClose}"
            )

        transition(name="fade")
            FormOrder(
                v-if="isPopupVisible"
                @closePopup="closeInfoPopup"
            )
    
</template>

<script>
    import FormOrder from "@/components/FormOrder.vue";

    export default {
        components: {
            FormOrder
        },
        props: ['burgerClose'],
        data() {
            return {
                isPopupVisible: false,
                cardlists: [
                    {id: 0, value:'11%', description: 'Вернем за покупки милями'},
                    {id: 1, value:'0%', description: 'Бесплатное снятие наличных по всему миру'},
                    {id: 2, value:'7%', description: 'До 7% на остаток по счету'},
                    {id: 3, value:'0р', description: 'Бесплатное годовое обслуживание'}
                ]
            }
        },
        methods: {
            onClickBurger(data) {
                this.burgerClose = data.burgerClose
            },
            closeInfoPopup() {
                this.isPopupVisible = false
            }
        }
    }
</script>

<style lang="scss">
    @import '@/assets/styles/main.scss';

    .your-card {
        margin-bottom: 272px;
        background: url('./../assets/img/bg.png') no-repeat center 116px;

        @media screen and (max-width: 1024px) {
            margin-bottom: 100px;
        }

        @media screen and (max-width: $tablet) {
            margin-bottom: 50px;
        }

        &__title {
            margin: 84px 0 60px 73px;
            font-family: 'Geometria';
            font-size: 96px;
            font-weight: 900;
            line-height: 109px;

            @media screen and (max-width: $tablet) {
                margin-top: 60px;
                margin-left: 20px;
                font-size: 52px;
                width: 60%;
                line-height: 62px;
            }

            @media screen and (max-width: $mobile) {
                margin: 0;
                margin-top: 50px;
                margin-bottom: 40px;
                margin-left: 10px;
                line-height: 50px;
                text-align: left;
                width: 100%;
            }

        }

        &__desc {
            margin-left: 37px;
            display: inline-block;
            width: 360px;
            font-size: 24px;
            line-height: 30px;
            color: $gray;

            @media screen and (max-width: $tablet) {
                font-size: 20px;
                margin-left: 0;
                margin-top: 20px;
                width: 100%;
            }

        }


        &__list {
            margin: 0 0 29px 74px;
            padding: 0;
            list-style: none;
            display: flex;
            flex-direction: row;
            flex-wrap: wrap;

            @media screen and (max-width: $tablet) {
                margin-left: 20px;
            }

            &-item {
                margin-bottom: 8px;
                margin-right: 53px;
                flex: 0 0 130px;

                @media screen and (max-width: $tablet) {
                    flex: 0 0 38%;
                }

                @media screen and (max-width: 425px) {
                    flex: 0 0 33%;
                }

                &:nth-child(odd) {
                    flex: 0 0 100px;

                    @media screen and (max-width: $tablet) {
                        flex: 0 0 38%;
                    }

                    @media screen and (max-width: 425px) {
                        flex: 0 0 33%;
                    }

                }

                &:nth-child(even) {
                    flex: 0 0 120px;
                    margin-right: 0;

                    @media screen and (max-width: $tablet) {
                        flex: 0 0 38%;
                        margin-right: 53px;
                    }

                    @media screen and (max-width: 425px) {
                        margin-right: 0;
                        flex: 0 0 40%;
                    }

                }

            }

            &-title {
                margin: 0;
                margin-bottom: -2px;
                font-family: Geometria;
                font-style: normal;
                font-weight: bold;
                font-size: 36px;
                line-height: 45px;
                color: $yellow;
                z-index: 10;
            }

            &-desc {
                font-family: Geometria;
                font-style: normal;
                font-weight: bold;
                font-size: 14px;
                line-height: 20px;
                color: $gray;
            }

        }

        &__card {
            top: 240px;
            right: -18px;
            position: absolute;
            transition: all .3s;

            @media screen and (max-width: 1850px) {
                right: 0;
                top: 340px;
                width: 55%;
            }

            @media screen and (max-width: 1200px) {
                right: 0;
                top: 410px;
                width: 60%;
            }

            @media screen and (max-width: 1024px) {
                right: 0;
                top: 480px;
                width: 60%;
            }

            @media screen and (max-width: $tablet) {
                right: 0;
                top: 110px;
                width: 54%;
            }

            @media screen and (max-width: 425px) {
                display: none;
            }

            &_active {

                @media screen and (min-width: 1840px) {
                    right: -120px;
                }

            }

        }

        &__button {
            padding: 27px 46px !important;
            margin: 35px 0 0 75px;
            line-height: 25px !important;

            @media screen and (max-width: $tablet) {
                margin-top: 20px;
                margin-left: 22px;
                padding: 22px 26px !important;
                font-size: 18px !important;
            }

            @media screen and (max-width: 425px) {
                width: 100%;
                margin: 0 auto !important;
                display: block;
            }

        }

    }
</style>
