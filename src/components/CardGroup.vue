<script>
import Card from '../components/Card.vue'

export default {
  components: {Card},

  data(){ return {  
      colors: ['gold', 'silver', 'orchid']
  }},

    methods: {  
      getCards () {  
        const cards = JSON.parse(window.localStorage.getItem('cards'))
        return cards
      },
    }
}
</script>

<template>
  <div class="card-wrapper">

    <Card 
      v-for="(card, index) in getCards()"
      :key="index"
    
      :card-number = "card.number"
      :first-name = "card.holder_first_name"
      :last-name = "card.holder_last_name"
      :Logo = "card.logo"
      :valid-month = "card.valid_till_month"
      :valid-year = "card.valid_till_year"
      @click.native="$emit('selected', card)" 
    >
    </Card>
      
  </div>
</template>

<style scoped>

  .card-wrapper {
   margin-top: 5rem;
   display: grid;
   grid-auto-rows: 3rem;
   margin-bottom: 14rem;
   

  }
 
</style>