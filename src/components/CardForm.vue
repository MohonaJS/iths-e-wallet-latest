<script>
import Card from './Card.vue'
export default {
    components:{Card},

    computed: {  
        month(){  
            return this.card.valid_till.split('-')[1];
            },
        year (){  
            return this.card.valid_till.split('-')[0];
            }
    },
    data(){
        return {  
          card: {  
            number: '',
            holder_first_name: '',
            holder_last_name:'',
            valid_till: '',
            vendor: null
        }
    }},
    methods: {  
        handleSubmit(){  
            const card = {  
                number: this.card.number,
                holder_first_name: this.card.holder_first_name,
                holder_last_name: this.card.holder_last_name,
                valid_till_month: this.month,
                valid_till_year: this.year,
                logo: this.card.vendor,

            }
            const cardsJson = window.localStorage.getItem('cards')
            const cards = JSON.parse(cardsJson)
            if(!cards){ 
                const cardsJson = JSON.stringify([card])
                window.localStorage.setItem('cards', cardsJson) 
            }else {  
                cards.push(card)
                window.localStorage.setItem('cards', JSON.stringify(cards))
            }
            this.$emit('change-view')
        }
    }
}
</script>

<template>
  <div class="formPage">
      <h1>ADD A NEW CARD</h1>
      <p>NEW CARD</p>
      <Card 
            :card-number ="card.number" 
            :first-name = "card.holder_first_name"
            :last-name = "card.holder_last_name"
            :valid-month= "month"
            :valid-year= "year"
            :Logo= "card.vendor"
      ></Card>
      
      <form @submit.prevent="handleSubmit">
          <div>
              <label for>CARD NUMBER</label>
              <input type="text" name="" v-model="card.number"/>
          </div>
          <div>
              <label for="">CardHolder FIRST NAME</label>
              <input type="text" name="" v-model="card.holder_first_name"/>
          </div>
          <div>
              <label for="">CardHolder LAST NAME</label>
              <input type="text" name="" v-model="card.holder_last_name"/>
          </div>
          <div>
              <label for="">VALID TILL</label>
              <input type="month" name="" v-model="card.valid_till"/>
          </div>
        
          <div>
              <label for="">VENDOR</label>
              <select name="" id="" v-model="card.vendor">
                  <option value="visa">VISA</option>
                  <option value="mastercard">MASTER</option>
              </select>
          </div>
          <button type="submit" > ADD  CARD </button>
      </form>
  </div>
</template>


<style scoped>
        form {
           padding: 20px; 
           background-color: rgb(12, 71, 73);
           color: white;
        }
        input, select  { 
            width: 100%;
            height: 2rem;
        }

        button { 
            background-color: teal;
            border: 4px solid white;
            color: white;
            padding: 15px 32px;
            text-align: center;
            font-size: 16px;
        }
        .formPage { 
            background-color: cadetblue;
        }
</style>