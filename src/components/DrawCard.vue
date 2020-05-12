<template lang='pug'>
    .draw
        .draw__container.container
            h2.draw__title Оформите свою новую карту для путешествий
            ul.draw__list.row
                li.draw__list-item.col-md-4(v-for="drawservice in drawservices" :key="drawservice.id")
                    p.draw__list-title
                        | {{ drawservice.before }}
                        span {{ drawservice.value }}
                    p.draw__list-desc {{ drawservice.description }}

            .order-card.row
                .col-lg-7.col-md-6
                    img.order-card__preview(src="./../assets/img/credit-card.png" alt="@@")

                .col-lg-5.col-md-6
                    .order-card__body
                        .order-card__tabs
                            a.order-card__tabs-link.order-card__tabs-link_active(href="#" title="") Кредитная карта
                            a.order-card__tabs-link(href="#" title="") Дебетовая карта
                        .order-card__button.button(@click="isPopupVisible = !isPopupVisible") Отправить заявку

                        ul.order-card__list
                            li.order-card__list-item
                                p.order-card__list-title Стоимость карты в год (руб.)
                                p.order-card__list-desc 6 490 (без пакета услуг), 4 990 (с пакетом услуг)
                            li.order-card__list-item
                                p.order-card__list-title Приветственные мили (шт.)	
                                p.order-card__list-desc 1 000
                            li.order-card__list-item
                                p.order-card__list-title Мили за покупки	
                                p.order-card__list-desc 5%

                        a.order-card__link(href="#" title="" @click.prevent="isPopupVisible = !isPopupVisible") Все подробности
        
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
        data() {
            return {
                isPopupVisible: false,
                drawservices: [
                    {id: 0, before: 'до', value: '11%', description:'Милями за услуги, оплаченные на travel.ru'},
                    {id: 1, before: 'до', value: '11%', description:'Милями за любые покупки по карте'},
                    {id: 2, value: '1 = 1', description:'Оплата милями билетов любых авиакомпаний по курсу 1 миля = 1 Р'},
                ]
            }
        },
        methods: {
            closeInfoPopup() {
                this.isPopupVisible = false
            }
        }
    }
</script>

<style lang="scss">
    @import '@/assets/styles/main.scss';
    
    .draw {
        margin-top: 178px;
       
        @media screen and (max-width: 1024px) {
            margin-top: 90px;
        }

        @media screen and (max-width: $tablet) {
            margin-top: 40px;
        }

        &__title {
            margin-left: 18px;
            margin-bottom: 49px;
            font-family: Geometria;
            font-size: 30px;
            line-height: 38px;
            letter-spacing: 0.3px;
            font-weight: bold;
            text-align: center;
            color: $white;
            z-index: 410;

            @media screen and (max-width: 425px) {
                margin-left: 0;
                font-size: 22px;
                line-height: 26px;
            }

        }

        &__list {
            margin: 0;
            padding: 0;
            list-style: none;
            margin: 0 auto !important;
            width: 850px !important;

            @media screen and (max-width: $tablet) {
                width: 100% !important;
            }

            &-item {
                padding: 0 45px !important;
                margin: 0 0 0;

                @media screen and (max-width: 425px) {
                    padding: 0 !important;
                    text-align: center;
                    margin-bottom: 20px;
                }

                &:nth-child(1) {
                    margin-left: 0px;
                }

                &:nth-child(2) {
                    margin-left: -4px;
                }

                &:last-child {
                    padding: 0 0 0 4px !important;
                }

            }

            &-title {
                margin: 0;
                padding: 0;
                font-family: Geometria;
                font-style: normal;
                font-weight: bold;
                font-size: 18px;
                line-height: 23px;
                color: $yellow;

                span {
                    font-family: Geometria;
                    font-style: normal;
                    font-weight: bold;
                    font-size: 36px;
                    line-height: 45px;
                    color: $yellow;
                }

            }

            &-desc {
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

    .order-card {
        margin-bottom: 74px;
        margin-top: 94px;

        @media screen and (max-width: 1024px) {
            margin-top: 60px;
            margin-bottom: 30px;
        }

        @media screen and (max-width: 425px) {
            margin-top: 30px;
            margin-bottom: 60px;
        }

        &__preview {
            margin: -1px 0 0 -25px;

            @media screen and (max-width: 1024px) {
                margin: 0;
                width: 96%;
            }

            @media screen and (max-width: $mobile) {
                width: 100%;
            }

        }

        &__body {
            margin: -6px 0 0 14px;

            @media screen and (max-width: $mobile) {
                margin: 0;
                margin-top: 20px;
            }

        }

        &__button {
            margin-top: -5px;
            margin-bottom: 67px;
            padding-left: 66px !important;
            padding-right: 66px !important;
            padding-top: 25px !important;
            padding-bottom: 25px !important;

            @media screen and (max-width: 1024px) {
                margin: -30px 0 20px 0;
            }

            @media screen and (max-width: $tablet) {
                padding: 20px 40px !important;
                font-size: 18px !important;
                margin-bottom: 30px;
                width: 100%;
            }

        }

        &__tabs {
            margin: 6px 0 50px -4px;
            display: flex;
            flex-direction: row;

            @media screen and (max-width: $mobile) {
                margin-top: 20px;
                padding: 0 4%;
                justify-content: space-between;
            }

            &-link {
                margin-right: 42px;
                font-family: Geometria;
                font-size: 18px;
                line-height: 23px;
                color: #6C6C6C;
                font-weight: bold;
                text-decoration: none;
                transition: all .3s;

                @media screen and (max-width: 1024px) {
                    margin-right: 40px;
                }

                @media screen and (max-width: $tablet) {
                    font-size: 16px;
                }

                @media screen and (max-width: 425px) {
                    margin-right: 0;
                }

                &:last-child {
                    @media screen and (max-width: 1024px) {
                        margin-right: 0;
                    }
                }

                &:hover {
                    color: $yellow;
                    text-decoration: underline;
                }

                &_active {
                    color: $yellow;
                }

            }

        }

        &__list {
            margin: -7px 0 29px -2px;
            padding: 0;
            list-style: none;

            @media screen and (max-width: 1024px) {
                margin-bottom: 8px;
            }

            &-item {
                display: flex;
                flex-direction: row;

            }

            &-title {
                margin: 0;
                width: 50%;
                margin-right: 10px;
                font-family: Geometria;
                font-size: 14px;
                line-height: 26px;
                color: $gray;
            }

            &-desc {
                margin: 0 0 0 14px;
                width: 50%;
                font-family: Geometria;
                font-size: 14px;
                line-height: 26px;
                color: #BBBBBB;
            }

        }

        &__link {
            margin-left: -1px;
            padding-bottom: 2px;
            font-family: Geometria;
            font-size: 14px;
            line-height: 26px;
            color: $yellow;
            text-decoration: none;
            border-bottom: 1px dashed $yellow;
            transition: all .3s;

            &:hover {
                color: $white;
                border-color: $white;
            }

        }

    }

</style>