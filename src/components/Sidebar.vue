<template lang='pug'>
    .sidebar(
        v-bind:class="{'sidebar_show' : burgerClose}"
    )
        ul.sidebar__navigation.navigation
            li.navigation__item
                a.navigation__link(href="#" title="") Какие преимущества
            li.navigation__item
                a.navigation__link(href="#" title="") Что вы получаете
            li.navigation__item
                a.navigation__link(href="#" title="") Еще сюрпризы
            li.navigation__item
                a.navigation__link(href="#" title="") Оформить карту

        .sidebar__contacts.contacts
            .contacts__item
                p.contacts__title По России
                a.contacts__phone(href="tel:88009506570" title="") 8 800 950 6570 
            .contacts__item
                p.contacts__title По Миру
                a.contacts__phone(href="tel:88009506570" title="") 8 800 950 6570
</template>

<script>
export default {
    props: ['burgerClose'],
    methods: {
        clickBurger: function() {
            this.burgerClose = !this.burgerClose
            this.onClickBurger( {
                burgerClose: this.burgerClose
            })
        }
    }
}
</script>

<style lang="scss">
    @import '@/assets/styles/main.scss';

    .sidebar {
        position: fixed;
        width: 393px;
        height: 100vh;
        background: $gray-dark;
        left: -393px;
        z-index: 11;
        opacity: 0;
        transition: all .3s;
        -webkit-transition: all .3s;

        &:before {
            @media screen and (max-width: 1840px) {
                right: -80px;
                top: -100px;
                display: block;
                position: absolute;
                content: '';
                width: 80px;
                height: 112vh;
                background: $black;
                opacity: 0.99;
            }
        }

        @media screen and (max-width: 1024px) {
            width: 40%;
        }

        @media screen and (max-width: 425px) {
            width: 80%;
        }

        &__navigation {
            margin: 93px 0 0 0 !important;
            padding: 0 0 0 100px !important;

            @media screen and (max-width: $tablet) {
                padding: 0 0 0 50px !important;
            }

            @media screen and (max-width: 425px) {
                margin-top: 40px !important;
            }

        }

        &_show {
            opacity: 1;
            left: 0;
        }

        &__contacts {
            left: 99px;
            bottom: 40px;
            position: absolute;

            @media screen and (max-width: $tablet) {
                left: 45px;
            }

        }

    }

    .navigation {
        margin: 0;
        padding: 0;
        list-style: none;
        width: auto;

        &__item {
            margin-bottom: 24px;
        }

        &__link {
            font-family: Geometria;
            font-style: normal;
            font-weight: bold;
            font-size: 18px;
            line-height: 30px;
            color: $white;
            text-decoration: none;
            transition: all .3s;

            &:hover {
                color: $yellow;
            }

        }

    }

    .contacts {

        &__item {
            margin-bottom: 0px;
        }

        &__title {
            margin: 18px 0 -10px 0;
            padding: 0;
            font-family: Geometria;
            font-size: 14px;
            line-height: 26px;
            color: $gray;
        }

        &__phone {
            margin: -20px 0 0 0;
            font-family: Geometria;
            font-size: 24px;
            line-height: 45px;
            color: #BBBBBB;
            text-decoration: none;
            transition: all .3s;

            &:hover {
                color: $yellow;
            }

        }
    }

</style>