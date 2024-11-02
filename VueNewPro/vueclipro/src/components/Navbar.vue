<template>
    <nav :class="[`navbar-${theme}`, `bg-${theme}`, 'navbar', 'navbar-expand-lg']">
      <a class="navbar-brand" href="#">Menu</a>
      <button
        class="navbar-toggler"
        type="button"
        data-toggle="collapse"
        data-target="#navbarNav"
        aria-controls="navbarNav"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav">
            <li v-for="(page, index) in pages" class="nav-item active" :key="index">
                <navbar-link
                :page ="page"
                :isactive="activePage == index"
                @click.prevent="navLinkClick(index)">
            </navbar-link>
          
          </li>
        </ul>
        <form class="d-flex">
          <button class="btn btn-primary" @click.prevent="changeTheme()">login</button>
        </form>
      </div>
    </nav>
  </template>
  
  <script>
  import NavbarLink from 'D:/Vue project/VueNewPro/vueclipro/src/components/NavbarLink.vue'
  export default {
    components:{
        NavbarLink,
    },
    name: 'AppNavbar',
    props: ['pages', 'activePage', 'navLinkClick'],
    created (){
        this.getThemeSetting();
    },
    data() {
      return {
        theme: 'light',
      };
    },
    methods: {
      changeTheme() {
        this.theme = this.theme === 'light' ? 'dark' : 'light';
        this.storeThemeSetting();
      },
      storeThemeSetting(){
        localStorage.setItem('theme',this.theme)

      },
      getThemeSetting(){
        let theme = localStorage.getItem('theme');
        if(theme){
            this.theme=theme;
        }

      }
    },
  };
  </script>
  