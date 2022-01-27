<script>
import Card from '../components/Card.vue'

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
      <h1>ADD A NEW BANK CARD</h1>
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
                  <option value="bitcoin">Bitcoin</option>
                  <option value="evil">Evil</option>
                  <option value="ninja">Ninja</option>
                  <option value="blockchain">Blockchain</option>
              </select>
          </div>
          <button type="submit" > ADD  CARD </button>
      </form>
  </div>
</template>

<style scoped>
        form {
           padding: 20px; 
          font-size: 20px;
           color: white;
        }
        input, select  { 
            width: 100%;
            height: 2rem;
        }

        button { 
             background-color: teal;
             color: white;
             padding: 15px 32px;
            cursor: pointer;
             margin-top: 1rem;
            font-size: 16px;
            width: 100%; background-color: teal;
     }
        label {
            font-size: 25px;
            font-weight: 500;
            display: block;
            margin: .8rem 0;
            color: black;
        }
</style>