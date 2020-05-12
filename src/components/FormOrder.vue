<template lang='pug'>
    .order
        .order__body
            .order__body-title(:class="{'hide': isValid}") Заявка на карту
            .button-close(@click="closePopup" :class="{'hide': isValid}")
                span.button-close__line
                span.button-close__line
            form.order__form(:class="{'hide': isValid}" method="post" action="/" @submit.prevent="onSubmit" novalidate)
                .input-group
                    .input-label(v-bind:class="{ 'input-group--error': $v.fio.$error, 'input-group--access': !$v.fio.$invalid}")
                        input.input(id="fio" type="text" name="fio" v-model.trim="$v.fio.$model" @change="$v.fio.$touch" required)
                        label(for="fio") ФИО
                        .error(v-if="!$v.fio.required || !$v.fio.alpha || !$v.fio.minLength") Некорректно введены данные
                        .error-icon(v-if="!$v.fio.required || !$v.fio.minLength || !$v.fio.alpha")
                            svg(width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg")
                                path(d="M2 18L10 10M18 2L10 10M10 10L18 18M10 10L2 2" stroke="#CC301B" stroke-width="3")
                        .access-icon(v-if="$v.fio.required && $v.fio.minLength")
                            svg(width="23" height="17" viewBox="0 0 23 17" fill="none" xmlns="http://www.w3.org/2000/svg")
                                path(d="M2 6.5L9.5 14L21.5 2" stroke="#89CC1B" stroke-width="3")

                .input-group
                    .input-label(v-bind:class="{ 'input-group--error': $v.email.$error, 'input-group--access': !$v.email.$invalid}")
                        input.input(id="email" type="text" name="email" v-model.trim="$v.email.$model" @change="$v.email.$touch" required)
                        label(for="email") Электронный адрес
                        .error(v-if="!$v.email.required || !$v.email.email") Электронный адрес некорректный
                        .error-icon(v-if="!$v.email.required || !$v.email.email")
                            svg(width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg")
                                path(d="M2 18L10 10M18 2L10 10M10 10L18 18M10 10L2 2" stroke="#CC301B" stroke-width="3")
                        .access-icon(v-if="$v.email.required && $v.email.email")
                            svg(width="23" height="17" viewBox="0 0 23 17" fill="none" xmlns="http://www.w3.org/2000/svg")
                                path(d="M2 6.5L9.5 14L21.5 2" stroke="#89CC1B" stroke-width="3")

                .input-group
                    .input-label(v-bind:class="{ 'input-group--error': $v.phone.$error, 'input-group--access': !$v.phone.$invalid}")
                        input.input(id="phone" type="text" name="phone" v-model.trim="$v.phone.$model" @change="$v.phone.$touch" required)
                        label(for="phone") Номер телефона
                        .error(v-if="!$v.phone.required || !$v.phone.numeric || !$v.phone.minLength") Некорректно введены данные
                        .error-icon(v-if="!$v.phone.required || !$v.phone.minLength || !$v.phone.numeric")
                            svg(width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg")
                                path(d="M2 18L10 10M18 2L10 10M10 10L18 18M10 10L2 2" stroke="#CC301B" stroke-width="3")
                        .access-icon(v-if="$v.phone.required && $v.phone.minLength")
                            svg(width="23" height="17" viewBox="0 0 23 17" fill="none" xmlns="http://www.w3.org/2000/svg")
                                path(d="M2 6.5L9.5 14L21.5 2" stroke="#89CC1B" stroke-width="3")

                .select-label
                    p.select-label__title Гражданство
                    v-select(:options="['Белорусь', 'Украина', 'Казахстан']" :clearable="false" v-model="selected" :searchable="false" id="gr")

                .checkbox-label
                    input.styled-checkbox(type="checkbox" id="consent2" v-model="consent")
                    label.styled-checkbox-1(for="consent2")
                        p Я соглашаюсь на <a class='checkbox-label__link' href="#" title="">обработку</a> моих персональных данных
                    
                button.order__button.button(type="submit" name="form-submit" :disabled="submitStatus === 'PENDING' || !consent || $v.$invalid" :class="{button_active: (consent || $v.$invalid)}") Заказать сейчас

            .order__message(v-if="submitStatus === 'OK'")
                .order__message-icon
                    svg(width="32" height="20" viewBox="0 0 24 19" fill="none" xmlns="http://www.w3.org/2000/svg")
                        path(d="M2 6.5L9.5 14L21.5 2" stroke="#89CC1B" stroke-width="3")
                h4.order__message-title Ваша заявка принята
                p В ближайшее время с вами свяжется наш менеджер
</template>

<script>
    import vSelect from "vue-select";
    import {required, minLength, email, helpers} from 'vuelidate/lib/validators';

    const alpha = helpers.regex('alpha', /[^a-zа-яё ]/iu);
    const numeric = helpers.regex('numeric', /^(\s*)?(\+)?([- _():=+]?\d[- _():=+]?){10,14}(\s*)?$/);

    export default {
        components: {
            vSelect
        },
        props: ['isPopupVisible'],
        
        data() {
            return {
                submitStatus: null,
                fio: '',
                email: '',
                phone: '',
                consent: false,
                isValid: false,
                selected: 'Российская федерация',
                ticketservices: [
                    {id: 0, title:'Билеты любых авиакомпаний', description: 'Предложения от 300+ авиакомпаний, 185+ lowcost перевозчиков, чартеры от 60 крупных российскихтуроператоров', img: '/img/icons/icon-1.svg'},
                    {id: 1, title:'Мили больше не сгорают', description: 'Мили, накопленные при оплате картой AlfaTravel, не сгорают и остаются на вашем счете, пока вы не решите их потратить', img: '/img/icons/icon-2.svg'},
                    {id: 2, title:'Продвинутая страховка – бесплатно', description: 'Расширенная страховка для всей семьи с учетом экстремальных видов спорта и алкоголя', img: '/img/icons/icon-3.svg'},
                    {id: 3, title:'Доступ к счетам в разных валютах', description: 'Текущие счета в рублях, долларах США, евро, английских фунтах стерлингов и швейцарских франках открываются в любой момент', img: '/img/icons/icon-4.svg'}
                ]
            }
        },
        methods: {
            onSubmit() {
                this.isValid = true,
                this.$v.$touch()
                if (this.$v.$invalid) {
                    this.submitStatus = 'ERROR'
                } else {
                    const order = {
                        fio: this.fio,
                        email: this.email,
                        phone: this.phone,
                        consent: this.consent
                    }
                    console.log(order)
                    this.submitStatus = 'PENDING'
                    setTimeout(() => {
                        this.submitStatus = 'OK'
                    }, 500)
                }
            },
            closePopup() {
                this.$emit('closePopup')
            }
        },
        validations: {
            fio: {
                required,
                alpha,
                minLength: minLength(10)
            },
            email: {
                required,
                email
            },
            phone: {
                required,
                minLength: minLength(10),
                numeric
            }
        }
    }
</script>

<style lang="scss">
    @import '@/assets/styles/main.scss';
    @import "vue-select/src/scss/vue-select.scss";

    .checkbox-label {
        margin: 8px 0 24px 0;
        
        @media screen and (max-width: 769px) {
            display: flex;
            flex-direction: row;
            justify-content: center;
        }

        @media screen and (max-width: 575px) {
            margin-top: 26px;
            text-align: center;
            display: flex;
            flex-direction: column;
            justify-content: center;
        }

        &__link {
            color: $white;
            text-decoration: none;

            &:hover {
                color: $yellow;
                text-decoration: underline;
            }

        }

        label {
            
            p {
                display: inline-block;
                color: $gray;
            }
        }

    }

    .select-label {
        position: relative;

        &__title {
            margin: 12px 0 0 31px;
            position: absolute;
            font-size: 14px;
            font-family: Geometria;
            font-style: normal;
            font-weight: 500;
            color: $gray;
            z-index: 30;
        }

        .vs__dropdown-toggle {
            padding: 0 27px;
            width: 100%;
            box-sizing: border-box;
            height: 80px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 10px;
            border: 0;
            outline: none;
            font-family: Geometria;
            font-style: normal;
            font-weight: 500;
            font-size: 20px;
            line-height: 113.22%;
            border: 0 !important;
            height: 80px;
        }

        .vs--open {
            background: #333333;
            border-radius: 10px;

            .vs__selected {
                margin: 34px 0 0 1px;
                padding: 0;
                font-weight: normal;
                color: $white !important;
                opacity: 1;
            }

            .vs__open-indicator {
                margin-top: -3px;
                margin-right: -3px;
            }

        }

        .vs__open-indicator {
            margin-top: -3px;
            margin-right: -3px;
        }

        .vs__selected {
            padding: 0;
            margin: 0;
            margin: 20px 0 0 2px;
            color: $white;

            @media screen and (max-width: 320px) {
                font-size: 14px
            }

        }

        .vs__dropdown-menu {
            margin-top: 5px;
            padding: 24px 10px;
            opacity: 1;
            background: #333333;
            border-radius: 10px;
            color: $white;

            li {
                margin-bottom: 16px;
                color: $white;
                font-family: Geometria;
                font-style: normal;
                font-weight: 500;
                font-size: 20px;

                &:hover {
                    background: 0;
                }

                &:last-child {
                    margin-bottom: 0;
                }
            }

        }

        .vs__open-indicator {
            fill: $white;
        }

    }

    .input-label {
        position: relative;
        width: 100%;
        height: auto;
        margin-bottom: 20px;

        label {
            top: 0;
            left: 0;
            margin: 26px 0 0 30px;
            position: absolute;
            transition: all 0.2s ease;
            font-family: Geometria;
            font-style: normal;
            font-weight: 500;
            font-size: 20px;
            color: $gray;
            z-index: 10;
        }       

        input:hover ~ label, input:focus ~ label, input:valid ~ label {
            margin: 14px 0 0 30px;
            font-size: 14px;
        }

        input {
            padding: 20px 30px 0 30px;
            transition: background 0.2s ease;
            display: inline-block;
            border: 0;


        }

    }

    .hide {
        display: none;
    }

    .order {
        top: 0;
        left: 0;
        position: fixed;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        width: 100%;
        height: 100%;
        background: $black-light;
        z-index: 20;

        .button-close {
            @media screen and (max-width: 769px) {
                top: 10px;
                right: 20px;
            }
        }

        &__message {
            display: flex;
            flex-direction: column;
            justify-content: center;
            text-align: center;

            &-icon {
                margin-bottom: 20px;
            }

            &-title {
                margin: 0;
                margin-bottom: 0px;
                font-family: Geometria;
                font-style: normal;
                font-weight: 800;
                font-size: 30px;
                line-height: 113.22%;
                font-weight: bold;
                text-align: center;
                color: $white;
            }

            &-desc {
                margin: 0;
                font-family: Geometria;
                font-style: normal;
                font-weight: 800;
                font-size: 14px;
                font-weight: bold;
                text-align: center;
                color: $gray;
            }

        }

        &__button {
            padding: 25px 47px !important;

            @media screen and (max-width: 575px) {
                width: 100%;
                font-size: 18px !important;
            }

        }

        &__body {
            position: relative;
            width: 680px;

            @media screen and (max-width: 1440px) {
                width: 100%;
                padding: 0 20px 0 20px;
            }

            &__form {
                width: 100%;
            }

            &-title {
                margin: 0;
                margin-bottom: 50px;
                font-family: Geometria;
                font-style: normal;
                font-weight: 800;
                font-size: 30px;
                line-height: 113.22%;
                font-weight: bold;
                text-align: center;
                color: $white;

                @media screen and (max-width: 425px) {
                    margin-top: 3px;
                    font-size: 24px;
                }

            }
        }

    }

    .error {
        margin: 10px 0 0 30px;
        font-family: Geometria;
        font-style: normal;
        font-weight: 500;
        font-size: 12px;
        color: #CC301B;
    }

    .error-icon {
        top: 32px;
        right: -34px;
        position: absolute;
        width: 16px;
        height: 16px;

        @media screen and (max-width: 769px) {
            right: 34px;
        }

    }

    .access-icon {
        top: 32px;
        right: -34px;
        position: absolute;
        width: 16px;
        height: 16px;

        @media screen and (max-width: 769px) {
            right: 34px;
        }

        svg {
            stroke: #89CC1B;
        }

    }

    .input-group--error {
        input {
            border: 1px solid #CC301B;
        }
    }

    .input-label {
        .error {
            display: none;
        }
        .error-icon {
            display: none;
        }
        .access-icon {
            display: none;
        }
        &.input-group--error, &.input-group--access {
            .error {
                display: block;
            }
            .error-icon {
                display: block;
            }
            .access-icon {
                display: none;
            }
        }

        &.input-group--access {
            .error {
                display: none;
            }
            .error-icon {
                display: none;
            }
            .access-icon {
                display: block;
            }
        }

    }

.styled-checkbox {
    position: absolute;
    opacity: 0;
  
    & + label {
      position: relative;
      cursor: pointer;
      padding: 0;
      outline: none;
      user-select:none;

        &:focus {
            outline: none;
        }

    }
  
    & + label:before {
      margin-top: -8px;
      content: '';
      margin-right: 20px;
      display: inline-block;
      vertical-align: text-top;
      width: 41px;
      height: 39px;
      background: rgba(255, 255, 255, 0.2);
      border-radius: 12px;
      transition: all .3s;
    }
  
    &:hover + label:before {
      background: rgba(255, 255, 255, 0.2);
    }
    
    &:focus + label:before {
      box-shadow: 0 0 0 3px rgba(0, 0, 0, 0.12);
      outline: none;
    }
    
    label {
        outline: none;
    }

    &:checked + label:before {
      background: rgba(255, 255, 255, 0.2);
    }
    
    &:disabled + label {
      color: #b8b8b8;
      cursor: auto;
      outline: none;
    }
  
    &:disabled + label:before {
      box-shadow: none;
      background: #ddd;
    }
  
    &:checked + label:after {
      content: '';
      position: absolute;
      left: 8px;
      top: 4px;
      width: 24px;
      height: 20px;
      background: url('./../assets/img/icons/check.svg') no-repeat;
      border-radius: 10px;

        @media screen and (max-width: 552px) {
            left: 45.5%;
        }

        @media screen and (max-width: 425px) {
            left: 44.5%;
        }

        @media screen and (max-width: 375px) {
            left: 43.5%;
        }

        @media screen and (max-width: 320px) {
            left: 42.5%;
        }

    }
  }

</style>