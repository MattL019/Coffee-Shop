<template>
  <div class="hometiles">
    
    <div class="tilegroup">
      <HomeTile v-for='(tile, index) in tileData' :key='index' :tileData='tile'/>
    </div>

  </div>  
</template>

<script>
import HomeTile from './HomeTile.vue';

export default {
  name: 'hometiles',
  components: {
    HomeTile
  },
  data: function() {
    return {
      tileData: [
        {
          title: 'SIT IN',
          desc: 'Enjoy our excellent sit-in deals and tremendous service.',
          id: 'sitin'
        },
        {
          title: 'TAKE AWAY',
          desc: 'Consume our tasty coffee from our unique takeaway cups.',
          id: 'takeaway'
        }, 
        {
          title: 'WIFI',
          desc: 'Use our public computers with free WiFi access for 1 hour per coffee purchased.',
          id: 'wifi'
        },
        {
          title: 'TRY OUR NEW LUNCH SPECIAL',
          id: 'special'
        }
      ]
    }
  }
}
</script>

<style lang="scss" scoped>
@import '@/styles/vars.scss';

  .hometiles {
    margin-top:40px;

    .tilegroup {
      width:90%;
      max-width:850px;
      margin:0 auto;

      @media(max-width:600px) {
        #sitin, #takeaway, #wifi, #special {
          position:relative;
        }

        #sitin { 
          margin-left:10px;
          z-index:3;
        }
        #takeaway {
          margin-top:-30px;
          z-index:2;
        }
        #wifi {
          margin-right:10px;
          margin-top:-30px;
          z-index:1;
        }
        #special {
          margin-top:-30px;
          z-index:2;
          height:auto;
        }
      }
      @media(min-width:600px) {
        display:flex;
        flex-wrap:wrap;
        justify-content:space-between;
        align-items:center;
        .hometile { margin: 0 0 50px 0; }
      }

      
    }



  }
</style>

