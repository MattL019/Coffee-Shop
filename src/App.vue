<template>
  <div id="app">

    <TheHeader/>

    <transition mode='out-in' name='route' enter-active-class='animated fadeIn faster' leave-active-class="animated fadeOut faster">
      <router-view/>
    </transition>

  </div>
</template>

<script>

// Components
import TheHeader from '@/components/TheHeader.vue';

export default {
  components: {
    TheHeader
  }
}
</script>


<style lang="scss">

@import './styles/normalize.css';
@import './styles/vars.scss';
@import './styles/animate.css';

* {
  box-sizing:border-box;
  font-family:$fnt;
}

#app {
  min-height:100vh;
  background-image:
    radial-gradient(rgba(black,.8), rgba($blk,.8)),
    url('./assets/bg.jpg');

  background-position:center center;
  background-size:cover;
  background-repeat:no-repeat;
}


</style>
