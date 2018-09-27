<template>
  <div class="theheader">
    <router-link tag='div' to='/' exact class="left">

      <div class="logomark">
        <img src="../assets/logomark.svg" alt="CS - Logo">
      </div>

      <transition name='logotype-anim'>
        <div class="logotype" v-if='!isHomePage'>
          <img src="../assets/logotype.svg" alt="Coffee Shop">
        </div>
      </transition>

    </router-link>

    <div class="right">

      <img @click='showMenu = !showMenu' id='menubtn' src="../assets/menubutton.svg" alt="Toggle Menu" title='Toggle Menu'>

      <transition name='menutoggle'>
        <ul class="menu" v-if='showMenu'>
          <router-link @click.native='showMenu = isMobile ? false : true' tag='li' v-for='(listItem, index) in menuList' :key='index' :to='listItem.to' :title='listItem.title' exact>
            {{listItem.name}}
          </router-link>

          <div class="socials">
            <img src="../assets/facebook.svg" alt="Facebook">
            <img src="../assets/twitter.svg" alt="Twitter">
          </div>
        </ul>
      </transition>

    </div>
  </div>
</template>

<script>
export default {
  name: 'theheader',
  data: function() {
    return {
      showMenu: true, // controls the toggle of menu
      menuList: [ // every menu list item
        {
          name: "HOME",
          to: '/',
          title: 'Go home' 
        },
        {
          name: "MENU",
          to: '/menu',
          title: 'View menu' 
        },
        {
          name: "DIRECTIONS",
          to: '/directions',
          title: 'See directions' 
        },
        {
          name: "CONTACT",
          to: "/contact",
          title: 'Contact us'
        },
      ]
    }
  },
  computed: {
    // Returns true if the user is on a small display (mobile)
    isMobile: function() { return window.outerWidth < 768; },
    isHomePage: function() { return this.$route.path === '/'; }
  },
  beforeMount: function() {
    if(this.isMobile) this.showMenu = false;
  }
}
</script>

<style lang="scss" scoped>

  @import '@/styles/vars.scss';

  .theheader {

    position:fixed;
    top:0;left:0;
    z-index:99;

    width:100%;

    display:flex;
    justify-content:space-between;
    align-items:center;

    // Background
    background-color:rgba(black,.5);
    padding:5px;

    .left {
      cursor:pointer;

      .logomark {
        img { width:35px;vertical-align:middle; }
      }
      .logotype {
        display:none;
      }

    }

    .right {
      
      #menubtn {
        width:25px;
        vertical-align:middle;
        filter:invert(100%);
      }

      .menu {
        list-style-type:none;
        padding:0;
        margin:0;

        position:fixed;
        left:0;top:45px;
        width:100%;
        height:calc(100vh - 45px);
        background-color:rgba($c2,.9);

        li {
          cursor:pointer;
          text-align:center;
          color:white;
          font-weight:900;
          font-size:2.5em;
          padding:15px 0;

          &:nth-child(even) {
            background-color:rgba(#DBAB79,.6);
          } 
        }

        .socials {
          // hide if screen is too short
          @media(max-height:500px) {
            display:none;
          }

          position:absolute;
          bottom:0;
          left:calc(50% - 80px);
          img {
            width:50px;
            filter:invert(100%);
            margin:15px;
            bottom:0;
          }
        }
      }

    }

    @media(min-width:1000px) {
      .left .logotype {
        display:inline-block;
        img {
          position:absolute;
          width:300px;
          top:20px;
        }
      }
    }

    @media(min-width:768px) {
      background-color:transparent;
      padding:0;

      .left {
        display:flex;

        .logomark {
          display:inline-block;
          position:relative;
          border-left:35px solid rgba(black,.5);
          border-top:35px solid rgba(black,.5);
          border-right:35px solid transparent;
          border-bottom:35px solid transparent;

          img {
            position:absolute;
            top:-20px;left:-20px;
            width:40px;
          }
        }
      }

      .right {
        margin-right:35px;

        #menubtn { display: none; }

        .menu {
          position:relative;top:0;
          height:auto;
          background-color:transparent;

          &::after {
            content:"";
            position:absolute;
            top:25px;
            left:0;
            width:100%;
            height:20px;
            background-color:rgba(black,.5);
            z-index:-1;

          }


          li {
            transition:ease-in-out.2s;
            display:inline-block;
            font-size:1.3em;
            font-weight:300;
            margin:0 20px;
            &:nth-child(even){background-color:transparent;}
            &.router-link-active::after {
              content:"";
              display:block;
              margin:0 auto;
              width:35px;
              padding-top:15px;
              border-bottom:2px solid $c2;
              transition:ease-in-out.2s;
            }
            &:hover {
              transform:translateY(-5px);
            }
          }


          .socials {display:none;}
        }
      }
    }

  }

  .menutoggle-enter-active, .menutoggle-leave-active {
    transition:ease-in-out .2s;
  }
  // Menu toggle transition
  .menutoggle-enter, .menutoggle-leave-to {
    opacity:0;
  }
  .menutoggle-enter-to, .menutoggle-leave {
    opacity:1;
  }

  .logotype-anim-enter-active {
    transition:ease-in-out 1s;
  }
  .logotype-anim-leave-active {
    transition:ease-in-out .5s;
  }
  .logotype-anim-enter, .logotype-anim-leave-to {
    opacity:0;
  }
  .logotype-anim-enter-to, .logotype-anim-leave {
    opacity:1;
  }

</style>