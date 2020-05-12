<template>
  <div id="app">
    <Sidebar :burgerClose="burgerClose"></Sidebar>
    <div
      v-if="onClickBurger"
      v-bind:class="{'main-container_active' : burgerClose}"
      class="main-container"
    >
      <Header :onClickBurger="onClickBurger"></Header>
      <YourCard :burgerClose="burgerClose"></YourCard>
      <BeginWithCard></BeginWithCard>
      <YouAreGetting></YouAreGetting>
      <PersonalAssistant></PersonalAssistant>
      <DrawCard></DrawCard>
      <Footer></Footer>
    </div>
  </div>
</template>

<script>
  import Sidebar from './components/Sidebar.vue'
  import Header from './components/Header.vue'
  import YourCard from './components/YourCard.vue'
  import BeginWithCard from './components/BeginWithCard.vue'
  import YouAreGetting from './components/YouAreGetting.vue'
  import PersonalAssistant from './components/PersonalAssistant.vue'
  import DrawCard from './components/DrawCard.vue'
  import Footer from './components/Footer.vue'

  export default {
    name: 'App',
    components: {
      Sidebar, Header, YourCard, BeginWithCard, YouAreGetting, PersonalAssistant, DrawCard, Footer
    },
    data() {
      return {
        burgerClose: false
      }
    },
    methods: {
      onClickBurger(data) {
        this.burgerClose = data.burgerClose
      }
    }
  }
</script>

<style lang='scss'>
  @import './assets/styles/bootstrap-grid.scss';
  @import './assets/styles/main.scss';
  @import './assets/styles/fonts.css';
</style>
