<template lang='pug'>
    footer.footer
        .footer__container.container
            .row
                .col-lg-3.col-md-12
                    img.footer__logo.logo(src="./../assets/img/logo.png" alt="@@")
                    p.footer__logo-desc АО «Кредит Европа Банк»
                .col-lg-3.col-md-6.col-12.col-sm-6
                    ul.footer__navigation
                        li.footer__navigation-item
                            a.footer__navigation-link(href="#" title="") О банке 
                        li.footer__navigation-item
                            a.footer__navigation-link(href="#" title="") Офисы и банкоматы
                        li.footer__navigation-item
                            a.footer__navigation-link(href="#" title="") Новости
                        li.footer__navigation-item
                            a.footer__navigation-link(href="#" title="") Вакансии
                        li.footer__navigation-item
                            a.footer__navigation-link(href="#" title="") Реализуемое имущество

                .col-lg-4.col-md-6.col-12.col-sm-6
                    ul.footer__navigation.footer__navigation_second
                        li.footer__navigation-item
                            a.footer__navigation-link(href="#" title="") Раскрытие информации
                        li.footer__navigation-item
                            a.footer__navigation-link(href="#" title="") Ставки по вкладам
                        li.footer__navigation-item
                            a.footer__navigation-link(href="#" title="") Условия и тарифы    
                        li.footer__navigation-item
                            a.footer__navigation-link(href="#" title="") Корпоративное управление    
                        li.footer__navigation-item
                            a.footer__navigation-link(href="#" title="") Карта сайта     

                .footer__contacts.contacts.col-lg-3.col-md-12
                    .contacts__item
                        p.contacts__title По России
                        a.contacts__phone(href="tel:88009506570" title="") 8 800 950 6570
                    .contacts__item
                        p.contacts__title По Миру
                        a.contacts__phone(href="tel:88009506570" title="") 8 800 950 6570
</template>

<style lang="scss" scoped>
    @import '@/assets/styles/main.scss';
    
    .footer {
        margin-bottom: 65px;
        margin-top: -74px;
        padding-top: 237px;
        background: url('./../assets/img/footer.png') no-repeat center 68px;
        
        @media screen and (max-width: 1024px) {
            padding-top: 200px;
            margin-bottom: 30px;
        }

        @media screen and (max-width: $tablet) {
            padding-top: 80px;
            margin-bottom: 30px;
        }

        &__container {
            position: relative;

            .col-lg-3:nth-child(2) {
                margin-left: 70px !important;

                @media screen and (max-width: $tablet) {
                    margin-left: 0px !important;
                }

            }
            .col-lg-3:nth-child(3) {
                margin-left: -70px !important;

                @media screen and (max-width: $tablet) {
                    margin-left: 0px !important;
                }

            }
        }

        &__logo {
            margin: 0 0 0 -27px;

            @media screen and (max-width: $tablet) {
                width: 240px;
                margin-left: 0px;
                margin: 0 auto;
            }

            @media screen and (max-width: $mobile) {
                width: 50%;
                margin: auto;
                display: block;
                margin-bottom: 0;
            }

            &-desc {
                margin: 8px 0 0 -25px;
                font-size: 14px;

                @media screen and (max-width: $tablet) {
                    margin-left: 0px;
                    margin-top: 0px;
                    margin-bottom: 40px;
                }

                @media screen and (max-width: $mobile) {
                    margin: auto;
                    margin-bottom: 40px;
                    width: 200px;
                    text-align: center;
                }

            }

        }

        &__navigation {
            margin: -2px 0px 0 20px;
            padding: 0;
            list-style: none;

            @media screen and (max-width: 1024px) {
                margin-left: 0;
            }

            @media screen and (max-width: $tablet) {
                margin-left: 4px;
            }

            @media screen and (max-width: $mobile) {
                margin-left: 0;
            }

            &_second {
                margin-left: -8px;

                @media screen and (max-width: 1024px) {
                    margin-left: -36px;
                }

                @media screen and (max-width: $tablet) {
                    margin-left: 0;
                }

            }

            &-item {
                height: auto;

                @media screen and (max-width: $mobile) {
                    text-align: center;
                }

            }

            &-link {
                font-family: Geometria;
                font-style: normal;
                font-weight: 500;
                font-size: 14px;
                line-height: 30px;
                color: $gray;
                text-decoration: none;
                transition: all .3s;

                &:hover {
                    color: $yellow;
                    text-decoration: underline;
                }

            }

        }

        &__contacts {
            right: -110px;
            position: absolute;
            overflow: hidden;

            @media screen and (max-width: 1024px) {
                right: -20px;
            }

            @media screen and (max-width: $tablet) {
                margin-top: 40px;
                position: relative;
                display: flex;
                flex-direction: row;
                justify-content: space-between;
                right: inherit;
            }

            @media screen and (max-width: $mobile) {
                margin: 0 auto;
                margin-top: 40px;
                width: 300px;
                position: relative;
                display: flex;
                flex-direction: column;
                justify-content: center;
                right: inherit;
            }

            .contacts__item {
                margin-bottom: 17px;

                @media screen and (max-width: $tablet) {
                    margin-left: 4px;
                    width: 50%;
                }

                @media screen and (max-width: $mobile) {
                    width: 100%;
                    margin-left: 0;
                    text-align: center;
                }

                &:last-child {
                    @media screen and (max-width: $tablet) {
                        margin-left: 24px;
                    }
                    @media screen and (max-width: $mobile) {
                        margin-left: 0;
                    }
                }

                .contacts__title {
                    margin-top: 0;
                    margin-bottom: -10px;
                }

                .contacts__phone {
                    margin-top: 0px;
                }

            }

        }

    }
</style>