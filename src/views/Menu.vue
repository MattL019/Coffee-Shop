<template>
  <div class="menu">

    <MenuDrinks/>

  </div>
</template>

<script>

// Components
import MenuDrinks from '@/components/Menu/MenuDrinks'

export default {
  name: 'menupage',
  components: {
    MenuDrinks
  }
}
</script>

<style lang="scss" scoped>

@import '@/styles/vars.scss';

.menu {
  padding-top:50px;
  padding-bottom:70px;

  @media(min-width:768px) {
    padding-top:120px;
  }

  @media(min-width:1000px) {
    padding-top:150px;
  }


}

</style>
