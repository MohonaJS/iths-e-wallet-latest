<template>
  <div id="app">
    <div>
      <CardDisplay v-if="visibleArea === 'card_display'" @change-view = "handleChangeView"> </CardDisplay> 

      <CardForm v-else  @change-view = "visibleArea = 'card_display'"> </CardForm>
    </div>
  </div>
</template>

<script>
  import CardDisplay from './components/CardDisplay'
  import CardForm from './components/CardForm'

export default {
  name: 'App',

  components: {
    CardDisplay,
    CardForm
  },

  data(){ return {  
      visibleArea : "card_display"
  }},

  methods: {  
    handleChangeView(){  
        this.visibleArea = 'form_display'
    }
  }
}
</script>

<style scoped>

#app {
  text-align: center;
  margin-top: 60px;
  color: rebeccapurple;
  text-align: center;
}
  
</style>
