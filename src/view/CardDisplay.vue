<script>
import Card from '../components/Card.vue'
import CardGroup from '../components/CardGroup.vue'

export default {
    components:{Card, CardGroup},

    data(){ return {  
        activeCard: {}
    }},

    methods: {  
        changeSelected(card){  
            this.activeCard = card
        }
    }
}
</script>

<template>
   <div>
      <header>
           <h1>E-WALLET</h1>
           <div>ACTIVE CARD</div>
      </header>

       <Card 
         class="card" 
        
         :card-number = "activeCard.number"
         :first-name ="activeCard.holder_first_name"
         :last-name = "activeCard.holder_last_name"
         :Logo = "activeCard.logo" 
         :valid-month="activeCard.valid_till_month"
         :valid-year="activeCard.valid_till_year"
         color="black"
       ></Card>

        <CardGroup @selected = "changeSelected"></CardGroup>

        <button class="add-card-button" @click="$emit('change-view')">ADD A NEW CARD</button>
   </div>
</template>

<style scoped>

    button {
         background-color: teal;
         color: white;
         padding: 15px 32px;
         margin-top: 3rem;
         font-size: 16px;
         width: 400px;
         margin: auto;
         cursor: pointer;
        }

    header { 
        height: 6rem;
    }
</style>