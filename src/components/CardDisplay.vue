<script>
import Card from './Card.vue'
import CardGroup from './CardGroup.vue'

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

        <!-- ekhan theke information patahbo -->
       <Card 
         class="card" 
         background-color = "orange" 
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
         margin-top: 1rem;
         font-size: 16px;
         width: 100%;
        }

    .card {
        margin-bottom: 2rem;
    }
    header { 
        height: 6rem;
    }
</style>