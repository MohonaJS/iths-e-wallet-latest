<script>
export default {
    props: {  
        BackgroundColor: {  
            default: 'orange'
        },
        Logo:{  
            default : 'ninja'
        },
        cardNumber: { 
            default: 'XXXX XXXX XXXX XXXX'
         },
         FirstName: {  
             default: 'FIRSTNAME'
         },
        LastName: {  
            default: 'LASTNAME'
        },
        ValidMonth: {  
            default: 'MM'
        },
        ValidYear: {  
            default: 'YY'
        },
        color: {  
            default : 'black'
        }
    },

    computed: {  
        cardNumbers : function() {  
            return this.cardNumber.split(' ')
        }
    }
}
</script>

<template>
    <div :class="['card', Logo]">
       <div class="header">
           <div style = "padding: 1rem;">
               <div> <img src="../assets/wifi.svg" alt=""> </div>
               <div> <img src="../assets/chip.svg" alt=""> </div>
           </div>

           <div>
               <img :src="require('../assets/'+Logo+'.svg')">
           </div>
       </div>
       <div class="number">
           <div v-for="(number, index) in cardNumbers" :key="index">{{number}}</div>
           
       </div>
        <div class="footer">
            <div>
                <div>CARD HOLDER NAME</div>
                <div>{{FirstName.toUpperCase() }}  {{LastName.toUpperCase() }}</div>
            </div>
            <div>
                <div>VALID TILL</div>
                <div>{{ValidMonth}} / {{ValidYear}}</div>
            </div>
        </div>
    </div>
</template>

<style scoped>
    .footer{
        margin-top: 2rem;
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        padding: 0.5rem;
    }
    .number {
        display: flex;
        justify-content: space-around;
    }
    .card { 
        width: 400px;
        margin: auto;
        height: 15rem;
        color: aliceblue;
        border-radius: 5px;
        font-weight: bolder;
        border: 2px solid rgb(94, 89, 89);
        cursor: pointer;
        
    }
    .header {
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        padding: 0.3rem;
        
         
    }
    .number { 
        display: flex;
        justify-content: space-around;
    }

    .bitcoin {
        background-color: #ffae34;
        color: black;
    }
    .blockchain {
        background-color: #8b58f9;
    }
    .evil {
        background-color: #f33355;
    }
    .ninja {
        background-color: #222222;
        color: white;
    }
</style>