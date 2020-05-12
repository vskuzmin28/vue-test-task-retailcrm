<template lang='pug'>
    header.header
        .header__container.container
            .header__burger.burger(
                v-on:click="clickBurger"
                v-bind:class="{'burger_close' : burgerClose}"
            )
                span.burger__line
                span.burger__line
                span.burger__line
            img.header__logo.logo(src="./../assets/img/logo.png" alt="@@")
</template>

<script>
export default {
    props: ['onClickBurger'],
    data() {
        return {
            burgerClose: false
        }
    },
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

<style lang="scss" scoped>
    @import '@/assets/styles/main.scss';
    
    .header {
        margin: 86px 0 0px 0;
        position: relative;

        @media screen and (max-width: $tablet) {
            margin-top: 44px;
        }

        &__burger {
            left: -9px;
            position: absolute;

            @media screen and (max-width: 1024px) {
                left: 88px;
            }

            @media screen and (max-width: $tablet) {
                left: 36px;
            }

        }

        &__logo {
            margin-left: 73px;
            height: 36px;

            @media screen and (max-width: 1024px) {
                margin-left: 140px;
            }

            @media screen and (max-width: $tablet) {
                zoom: 0.8;
                margin-left: 100px;
            }

            @media screen and (max-width: 425px) {
                zoom: 0.6;
                margin-left: 120px;
            }

        }

        &__container {
            position: relative;
            display: flex;
            flex-direction: row;
            align-items: center;
        }

    }

    .burger {
        width: 25px;
        height: 19px;
        cursor: pointer;
        
        &__line {
            margin-bottom: 5px;
            display: block;
            width: 100%;
            height: 3px;
            background: $yellow;
            transition: all .3s;

            &:nth-child(2) {
                width: 20px;
            }

            &:last-child {
                margin-bottom: 0;
            }
        }

        &:hover {
            .burger__line {
                background: $yellow-dark;
            }
        }

        &_close {
            left: 489px;
            top: 96px;
            position: fixed;
            z-index: 20;

            &:before {
                @media screen and (max-width: 1840px) {
                    left: -30px;
                    top: -100px;
                    display: block;
                    position: absolute;
                    content: '';
                    width: 80px;
                    height: 100vh;
                }
                
            }

            @media screen and (max-width: 1840px) {
                left: 420px;
            }

            @media screen and (max-width: 1024px) {
                top: 46px;
                left: 438px;
            }

            @media screen and (max-width: $tablet) {
                left: 334px;
            }

            @media screen and (max-width: 425px) {
                top: 46px;
                left: inherit;
                right: 7%;
            }

            .burger__line {
                position: absolute;
                transition: all .3s;

                @media screen and (max-width: 1440px) {
                    background: $yellow !important;
                }

                &:nth-child(1) {
                    margin: 8px 0 0 0;
                    transform: rotate(45deg);
                }

                &:nth-child(2) {
                    opacity: 0;
                }

                &:last-child {
                    margin: 8px 0 0 0;
                    transform: rotate(-45deg);
                }

            }
        }

    }
</style>