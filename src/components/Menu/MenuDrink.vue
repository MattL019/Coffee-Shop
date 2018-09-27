<template>
  <div class="menudrink">

    <div class="diagram">
      <div class="diagram-parts">
        <div class='diagram-part' v-for='(ingred, index) in drinkData.recipe' :key='index' :class='index' :style='{height: ingred}'>
          {{index | format }}
        </div>
      </div>

      <span class="price">£{{drinkData.price}}</span>
  
    </div>

    <div class="label">
      <h1>{{drinkData.name}}</h1>
      <p>{{drinkData.desc}}</p>
    </div>


  </div>
</template>

<script>
export default {
  name: 'menudrink',
  props: {
    drinkData: Object
  },
  filters: {
    format: function(value) {
      if(!value) return '';
      return value.toUpperCase().replace(/-/g, " ");
    }
  }
}
</script>

<style lang="scss" scoped>
@import '@/styles/vars.scss';

  .menudrink {
    margin:15px;

    .diagram {
      position:relative;
      width:225px;
      height:225px;
      margin-bottom:5px;
      border:4px solid white;
      background-color:rgba(white,.2);

      box-shadow: inset 0 0 25px rgba(black,.2);

      .price {
        color:white;
        position:absolute;
        bottom:0;right:0;
        font-weight:300;
        background-color:rgba(black,.2);
        padding:4px;
      }

      .diagram-parts {
        height:100%;
        transform-origin:center bottom;
        animation:fillUp 2s forwards;

        display:flex;
        flex-direction:column;
        justify-content:flex-end;
      }

      .diagram-part {
        display:flex;
        align-items:center;
        justify-content:center;
        color:rgba(white,.6);
        font-size:1.2em;
        font-weight:800;
        text-align:center;

        // Colour codes
        &.espresso {background-color:$espresso;}
        &.milk-foam {background-color:$milkfoam;}
        &.whipped-cream {background-color:$whippedcream;}
        &.steamed-milk {background-color:$steamedmilk;color:white;}
        &.steamed-half-and-half {background-color:$steamedhalfandhalf;color:white;}
        &.chocolate-syrup {background-color:$chocolatesyrup;}
      }
    }

    .label {
      h1, p { margin:2px 0 0 0; color:white; }
      h1 {
        font-size:1.4em;
        font-weight:500;
      }
      p {
        line-height:1.5em;
        color:rgb(230,230,230);
      }
    }
  }

@keyframes fillUp {
  from {
    transform:scaleY(0);
  }
  to {
    transform:scaleY(1);
  }
}


</style>
