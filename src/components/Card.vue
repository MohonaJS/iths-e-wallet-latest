<script>
export default {
    props: {  
        BackgroundColor: {  
            default: 'gray'
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
            default : 'white'
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
    <div class="card" :style="'background-color:'+ BackgroundColor  + ';color: ' + color ">
       <div class="header">
           <div style = "padding: 1rem;">
               <div>WIFI</div>
               <div>SIM</div>
           </div>

           <div style = "padding: 1rem;">
               {{Logo.toUpperCase()}}
           </div>

        <!--    <div>
               <img :src="require('../assets/'+Logo+'.svg')">
           </div> -->
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
        justify-content: space-between;
    }
    .number {
        display: flex;
        justify-content: space-around;
    }
    .card { 
        width: 100%;
        height: 10rem;
        background-color: rgb(135, 56, 56);
        color: aliceblue;
        border-radius: 5px;
        font-weight: bolder;
        
    }
    .header {
        display: flex;
        justify-content: space-between;
         
    }
    .number { 
        display: flex;
        justify-content: space-around;
    }
</style>