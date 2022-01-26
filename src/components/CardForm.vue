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
      <hr>
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
              <label for="">CARDHOLDER FIRST NAME</label>
              <input type="text" name="" v-model="card.holder_first_name"/>
          </div>
          <div>
              <label for="">CARDHOLDER LAST NAME</label>
              <input type="text" name="" v-model="card.holder_last_name"/>
          </div>
          <div>
              <label for="">VALID TILL</label>
              <input type="month" name="" v-model="card.valid_till"/>
          </div>
        
          <div>
              <label for="">VENDOR</label>
              <select name="" id="" v-model="card.vendor">
                  <option value="Bitcoin">Bitcoin</option>
                  <option value="Blockchain">Blockchain</option>
                  <option value="Evil">Evil</option>
                  <option value="Ninja">Ninja</option>
              </select>
          </div>
          <button type="submit" > ADD  CARD </button>
      </form>
  </div>
</template>


<style scoped>
        form {
           padding: 20px; 
           background-color: rgb(17, 60, 61);
           color: white;
           font-size: 20px;
        }
        input, select  { 
            width: 100%;
            height: 2rem;
        }
        label {
            font-size: 25px;
            padding: 10px;
            font-weight: 500;
            display: block;
            margin: .8rem 0;
        }

        button { 
            background: linear-gradient(135deg, #746c73 0%, #084352 100%);
            border: 4px solid white;
            width: 100%;
            color: white;
            letter-spacing: 0.3rem;
            padding: 15px;
            text-align: center;
            font-size: 26px;
            margin: 15PX;
            box-shadow: aliceblue;
            border-radius: 50px;
        }
        
       
</style>