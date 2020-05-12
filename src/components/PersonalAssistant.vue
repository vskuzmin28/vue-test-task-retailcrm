<template lang='pug'>
    .assistant
        .assistant__container.container
            h2.assistant__title Персональный помощник
            p.assistant__desc 
                | Бесплатно для владельцев 
                span CARD PLUS
            img.assistant__row-mask(src="./../assets/img/bg2.png" alt="@@")
            .row.assistant__row
                .col-lg-7.col-md-12
                    img.assistant__woman(src="./../assets/img/assistant.png" alt="@@")
                .col-lg-3.col-md-12
                    ul.assistant__list
                        li.assistant__list-item(v-for="personalservice in personalservices" :key="personalservice.id")
                            img.assistant__list-preview(:src="personalservice.img" alt="@@")
                            p.assistant__list-title {{ personalservice.description }}
</template>

<script>
export default {
    data() {
        return {
            personalservices: [
                {id: 0, description:'Организует встречи, найдет гидов и переводчиков', img: '/img/icons/icon-5.svg'},
                {id: 1, description:'Спланирует поездку по самым интересным местам вашего отдыха', img: '/img/icons/icon-6.svg'},
                {id: 2, description:'Достанет билеты на мероприятия, даже если их уже нет в продаже', img: '/img/icons/icon-7.svg'},
                {id: 3, description:'Закажет столик в ресторане, клубе или кафе', img: '/img/icons/icon-8.svg'}
            ]
        }
    }
}
</script>

<style lang="scss">
    @import '@/assets/styles/main.scss';
    
    .assistant {
        position: relative;
        margin-top: 92px;
        background: url('./../assets/img/bg.png') no-repeat center;

        @media screen and (max-width: 1024px) {
            margin-top: 30px;
        }

        &__row {
            margin: 0 auto !important;
            width: 900px !important;

            @media screen and (max-width: $tablet) {
                width: 100% !important;
            }

            &-mask {
                left: 0;
                bottom: -100px;
                position: absolute;
                width: 100%;
                height: 215px;
                z-index: 10;

                @media screen and (max-width: $tablet) {
                    bottom: 180px;
                    width: 100%;
                    height: auto;
                }

                @media screen and (max-width: 425px) {
                    display: none;
                }

            }

        }

        &__title {
            margin: 0 0 0 18px;
            padding: 0;
            font-family: Geometria;
            font-weight: bold;
            font-size: 30px;
            line-height: 38px;
            letter-spacing: 0.3px;
            text-align: center;
            color: $white;

            @media screen and (max-width: 425px) {
                margin-left: 0;
                font-size: 22px;
                line-height: 26px;
            }

        }

        &__desc {
            margin: 0;
            margin-top: 15px;
            margin-left: 15px;
            margin-bottom: 60px;
            padding: 0;
            font-family: Geometria;
            font-size: 14px;
            line-height: 18px;
            color: $white;
            text-align: center;
            font-weight: bold;

            span {
                color: $yellow;
                text-transform: uppercase;
            }
        }

        &__woman {
            margin-top: 3px;
            margin-left: 54px;

            @media screen and (max-width: $tablet) {
                width: 40%;
                margin: 0;
            }
            
            @media screen and (max-width: 425px) {
                display: none;
            }

        }

        &__list {
            position: absolute;
            width: 250px;
            margin: 76px 0 0 60px;
            padding: 0;
            list-style: none;

            @media screen and (max-width: 1024px) {
                margin-left: -30px;
                width: 300px;
            }

            @media screen and (max-width: $tablet) {
                margin-top: 26px;
                width: 100%;
                position: relative;
                display: flex;
                flex-direction: row;
                flex-wrap: wrap;
                z-index: 100;
            }

            @media screen and (max-width: 425px) {
                margin-top: 0;
                flex-wrap: nowrap;
                flex-direction: column;
                margin-left: 0;
            }

            &-preview {
                margin-right: 17px;

                @media screen and (max-width: 425px) {
                    margin-right: 0;
                }

            }

            &-item {
                margin-bottom: 17px;
                display: flex;
                flex-direction: row;

                @media screen and (max-width: $tablet) {
                    width: 50%;
                    padding: 0 26px 0 46px;
                }

                @media screen and (max-width: 425px) {
                    flex-direction: column;
                    padding: 0;
                    width: 100%;
                }

                &:last-child {
                    margin-top: 18px;
                    margin-left: 8px;
                    width: 220px;

                    @media screen and (max-width: $tablet) {
                        width: 50%;
                        margin-left: 0;
                    }

                    @media screen and (max-width: 425px) {
                        width: 100%;
                        margin-left: 0;
                    }

                }

            }

            &-title {
                font-family: Geometria;
                font-size: 14px;
                line-height: 20px;
                font-weight: bold;
                color: $white;

                @media screen and (max-width: 425px) {
                    text-align: center;
                    width: 60%;
                    margin: 0 auto;
                    margin-top: 16px;
                    margin-bottom: 30px;
                }

            }

        }

    }

    .assistant__row {

        .col-md-12 {

            @media screen and (max-width: $tablet) {
                display: flex;
                justify-content: center;
            }

        }

    }
    
</style>