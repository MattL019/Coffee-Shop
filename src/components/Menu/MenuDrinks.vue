<template>
  <div class="menudrinks">

    <div class="introduction">
      <h1>Drinks Menu</h1>
      <p>View our large variety of coffee's. Happy drinking!</p>

    </div>

    <MenuDrink v-for='(drink, index) in drinksList' :key='index' :drinkData='drink'/>

  </div>
</template>

<script>
import MenuDrink from './MenuDrink.vue';

// Import drinks data
import drinks from '@/drinks';

export default {
  name: 'menudrinks',
  components: {
    MenuDrink
  },
  data: function() {
    return {
      drinksList: drinks
    }
  }
}
</script>

<style lang="scss" scoped>
@import '@/styles/vars.scss';

  .menudrinks {

    display:flex;
    flex-wrap:wrap;
    padding:10px 50px;

    background-image:linear-gradient(135deg,rgba($c2,.3) 20%,rgba($c2,.1));
    
    .introduction {
      padding:15px;
      width:225px;
      margin:15px;
      background-image:linear-gradient(135deg,rgba($c3,.6),transparent);
      color:white;
      h1,p{margin:0;}
      h1 {
        font-weight:800;
        font-size:3em;
      }
      p {
        font-size:1.2em;
        line-height:1.5em;
        margin-top:10px;
      }
    }



  }
</style>
