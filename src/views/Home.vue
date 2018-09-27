<template>
  <div class="home">

    <div class="logotype">
      <img src="../assets/logotype.svg" alt="Coffee Shop">
    </div>

    <HomeNavigation/>

    <HomeTiles/>

  </div>
</template>

<script>

// Components
import HomeNavigation from '@/components/Home/HomeNavigation';
import HomeTiles from '@/components/Home/HomeTiles';

export default {
  name: 'home',
  components: {
    HomeNavigation,
    HomeTiles
  }
}
</script>

<style lang="scss" scoped>

@import '@/styles/vars.scss';

.home {
  padding-top:70px;
  padding-bottom:70px;

  .logotype {
    width:320px;
    margin:0 auto;
  }

  @media(min-width:1000px) {
    .logotype {
      width:520px;
    }
  }
}

</style>
