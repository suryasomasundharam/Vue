 <template>
 <a
      class="nav-link"
      :class="activeclasses"
      aria-current="page"
      :href="page.links.url"
      :title="`this page going to ${page.links.text}`"
      
      >{{ page.links.text }}</a >
    </template>

    <script>
    export default{
        props :['page','isactive'],
        computed : {
            activeclasses(){
                return {
                    active : this.isactive,
                    emphasize : this.isactive
                }
            }
        }
    }
    </script>
    <style scoped>
    .emphasize {
        text-decoration : underline !important ;
     }
    </style>
 