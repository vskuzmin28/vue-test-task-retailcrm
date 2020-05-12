<template lang='pug'>
    .getting
        .container
            h2.getting__title Мы позаботились, чтобы вы получили
            ul.getting__list.row
                li.getting__list-item.col-lg-4.col-md-6(v-for="service in services" :key="service.id")
                    img.getting__list-preview(:src="service.img" alt="@@")
                    p.getting__list-title {{ service.title }}
                    p.getting__list-desc {{ service.description }}
                    ul.getting__list-partners
                        li.getting__list-partners__item(v-for="partner in service.partners" :key="partner.id")
                            img(:src="partner.img" alt="@@")
                             
</template>

<script>
export default {
    data() {
        return {
            services: [
                {id: 0, title: 'Бесплатный безлимитный интернет в роуминге', img: '/img/services/service-1.png', 
                    partners: [
                        {id: 1, img: '/img/partners/partner-1.png'},
                        {id: 2, img: '/img/partners/partner-2.png'},
                        {id: 3, img: '/img/partners/partner-3.png'},
                        {id: 4, img: '/img/partners/partner-4.png'}
                    ]
                },
                {id: 1, title: 'Бесплатная упаковка багажа', description: 'Держатели карт Visa Signature могут упаковать багаж в крупных аэропортах России', img: '/img/services/service-2.png'},
                {id: 2, title: 'Бесплатный доступ в приложении App In The Air', description: 'Бесплатная премиум подписка при покупке авиабилетов на travel.alfabank.ru', img: '/img/services/service-3.png'},
                {id: 3, title: 'Такси бизнес-класса со скидкой 20%', img: '/img/services/service-4.png',
                    partners: [
                        {id: 1, img: '/img/partners/partner-5.png'},
                        {id: 2, img: '/img/partners/partner-6.png'}
                    ]
                },
                {id: 4, title: 'Скидка в ресторанах Novikov Group в аэропорту Шереметьево', img: '/img/services/service-5.png'},
                {id: 5, title: 'Доступ в бизнес-залы Priority Pass по всему миру', img: '/img/services/service-6.png'}
            ]
        }
    }
  }
</script>

<style lang="scss">
    @import '@/assets/styles/main.scss';
    
    .getting {
        margin: 0 auto;
        margin-top: 153px;
        padding: 0;
        width: 1040px;
       
        @media screen and (max-width: 1024px) {
            margin-top: 70px;
            width: 100%;
        }

        &__title {
            margin: 0 0 72px 15px;
            padding: 0;
            font-family: Geometria;
            font-size: 30px;
            line-height: 38px;
            letter-spacing: 0.35px;
            color: $white;
            text-align: center;

            @media screen and (max-width: 425px) {
                margin-left: 0;
                font-size: 22px;
                line-height: 26px;
                margin-bottom: 40px;
            }

        }

        &__list {
            margin: 0;
            padding: 0;
            list-style: none;

            &-item {
                padding: 0 31px !important;
                margin-bottom: 39px;
                margin-left: 2px;

                @media screen and (max-width: $tablet) {
                    margin-left: 0;
                }

                &:nth-child(3n+3) {
                    margin-right: -10px;

                    @media screen and (max-width: $tablet) {
                        margin-right: 0;
                    }

                }

                &:nth-child(4) {
                    .block-you-are-getting__list-partners {
                        margin: -12px 0 0 0;

                        .block-you-are-getting__list-partners__item:nth-child(3) {
                            margin: -30px 0 0 0;
                        }

                    }
                }

            }

            &-title {
                margin: 23px 0 0px 7px;
                padding: 0;
                width: 90%;
                font-family: Geometria;
                font-size: 18px;
                font-weight: bold;
                line-height: 23px;
                color: $white;
            }

            &-desc {
                margin: 8px 0 0 7px;
                font-family: Geometria;
                font-size: 14px;
                font-weight: bold;
                line-height: 20px;
                color: $gray;
            }

            &-preview {
                margin-left: 2px;
                width: 100%;
                height: auto;
            }

            &-partners {
                margin: 10px 0 0 0;
                padding: 0;
                list-style: none;
                display: flex;
                flex-direction: row;
                flex-wrap: wrap;
                align-items: flex-end;

                &__item {
                    margin-top: 16px;
                    margin-left: 3px;
                    margin-bottom: 5px;
                    margin-right: 28px;
                    display: flex;
                    align-items: flex-end;
                }

            }

        }

    }
</style>