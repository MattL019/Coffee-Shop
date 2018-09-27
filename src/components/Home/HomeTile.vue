<template>
  <div class="hometile" :id='tileData.id'>
    <h1>{{tileData.title}}</h1>
    <p>{{tileData.desc}}</p>
  </div>
</template>

<script>
export default {
  name:'hometile',
  props: {
    tileData: Object
  }
}
</script>

<style lang="scss" scoped>
@import '@/styles/vars.scss';

  .hometile {
    width:250px;
    height:250px;
    margin:0 auto;

    padding:20px;

    background-position:center;
    background-size:cover;
    background-repeat:no-repeat;

    border:4px solid $c2;

    display:flex;
    flex-direction:column;
    justify-content:center;
    align-items:center;

    &#sitin { 
      background-image: 
        linear-gradient(135deg, #636363, rgba(white,.2)),
        url('../../assets/sitin.jpg'); 
    }
    &#takeaway { 
      background-image: 
        linear-gradient(135deg, #636363, rgba(white,.2)),
        url('../../assets/takeaway.jpg'); 
    }
    &#wifi { 
      background-image: 
        linear-gradient(135deg, #636363, rgba(white,.2)),
        url('../../assets/wifi.jpg'); 
    }
    &#special {
      font-size:.6em;
      background-image: 
        linear-gradient(135deg, #636363, rgba(white,.2)),
        url('../../assets/lunch.jpg'); 
    }

    h1, p {
      color:white;
      margin:0;
      text-align:center;
    }

    &#special h1, &#special p { text-align:left; }

    h1 {
      font-weight:800;
      font-size:2.5em;
    }
    p {
      line-height:1.5em;
      text-shadow:0 0 5px rgba(black,.5);
    }

    @media(min-width:1000px) {
      height: 420px;
      display:inline;
      padding-top:60px;
      
      &#special {
        width:100%;
        height:auto;
        padding:15px;
      }
    }

  }
</style>

