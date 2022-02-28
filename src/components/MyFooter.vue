  <template>
      <v-app>
    <v-footer
      class="bg-indigo-lighten-1 text-white text-center d-flex flex-column"
      height="70"
      
      
    >
     
  
      <div class="text-white pt-0">
      </div>
  
      <v-divider></v-divider>
  
      <div class="text-white">
        {{ new Date().getFullYear() }} — <strong>Vuetify</strong>
      </div>
    </v-footer>
  </v-app>
  </template>

<script>
export default{
    name: 'MyFooter',
    
    data:() =>({
        
    })
}
</script>

<style>

</style>