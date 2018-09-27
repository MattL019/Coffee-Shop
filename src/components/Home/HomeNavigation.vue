<template>
  <ul class="homenavigation">

    <router-link tag='li' to='/menu' title='View menu' exact>MENU</router-link>
    <div class="dash"></div>
    <router-link tag='li' to='/directions' title='See directions' exact>DIRECTIONS</router-link>
    <div class="dash"></div>
    <router-link tag='li' to='/contact' title='Contact us' exact>CONTACT</router-link>

  </ul>
</template>

<script>
export default {
  name: 'homenavigation',
}
</script>

<style lang="scss" scoped>
@import '@/styles/vars.scss';

  .homenavigation {
    list-style-type:none;
    margin:0;
    padding:0;

    width:100%;
    background-color:rgba($c2,.7);

    display:flex;
    justify-content:center;
    align-items:center;
    flex-wrap:wrap;

    li {
      cursor:pointer;
      display:inline-block;
      color:white;
      font-weight:700;
      font-size:1.3em;
      margin:8px;
      text-align:center;
      transition:ease-in-out.2s;
      &:hover {
        transform:scale(1.1);
      }
    }

    @media(min-width:1000px) {
      li {
        font-size:1.8em;
      }

      .dash {
        width:40px;
        height:4px;
        margin:0 10px;
        background-color:rgba(white,.8);
      }
    }
  }
</style>
