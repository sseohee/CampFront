<template>
  <v-card
    tile
    style="width: 100%" 
  >
    <v-list rounded>
      <v-subheader>Popular CampingSite</v-subheader>
      <v-list-item-group
        v-model="selectedItem"
        color="primary"
      >
        <v-list-item
          v-for="(popular, i) in populars"
          :key="i"
        >
          <v-list-item-content>
            <v-title v-text="popular.title"></v-title>
          </v-list-item-content>
          <v-list-item-content>
            <v-list-item-title v-text="popular.campingsite"></v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list-item-group>
    </v-list>
  </v-card>
</template>

<script>

import popularApi from '@/api-ajax/popular';

export default {
 data(){
     
     return {
         populars:[],
         selectedItem: 1
     }
 },
 created(){
     popularApi.getPopular().then(res => {
     this.populars =[].concat(res.data);
     

     })
 }
}
</script>