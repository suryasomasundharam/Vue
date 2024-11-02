<template>
  <div>
    <AppNavbar
      :pages="pages"
      :active-page="activePage"
      :nav-link-click="handleNavLinkClick"
    />
    <PageViewer 
    v-if="pages.length > 0"
    :page="pages[activePage]" ></PageViewer>
     

    <create-page
    :page-created="pageCreated"
    >
    </create-page>
  </div>
</template>

<script>
import AppNavbar from './components/Navbar.vue';
import PageViewer from './components/PageViewer.vue';
import CreatePage from './components/CreatePage.vue';

export default {
  components: {
    AppNavbar,
    PageViewer,
    CreatePage
  },
  created(){
    this.getPages();
  },
  data() {
    return {
      activePage: 0,
      pages: []
    };
  },
  methods: {
    handleNavLinkClick(index) {
      this.activePage = index;
    },
  async getPages(){
     let res =await fetch('pages.json');
     let data = await res.json();
     this.pages = data;
  },
  pageCreated(pageObj){
           console.log(pageObj);
  }
},
};
</script>
