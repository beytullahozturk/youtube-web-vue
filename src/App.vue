<template>
  <v-app>
  <!-- Navigation Menu Start -->
  <v-navigation-drawer v-model="drawer" app clipped floating temporary>
    <v-list dense>
        <v-row class="ma-3">
          <v-icon class="mx-4">mdi-video</v-icon>
          <v-toolbar-title class="align-center">
          <span class="title">YouTube</span>
          </v-toolbar-title>
        </v-row>
        <v-divider/>
        <v-row class="ma-2">
          <v-list-item v-for="item in items" :key="item.icon" link>
          <v-list-item-actions>
            <v-icon>{{item.icon}}</v-icon>          
          </v-list-item-actions>
          <v-list-content class="ml-2">
            <v-lis-item-title>{{item.text}}</v-lis-item-title>
          </v-list-content>
        </v-list-item>
        </v-row>
    </v-list>
  </v-navigation-drawer>
  <!-- Navigation Menu Stop -->
  <!-- Header Start -->
   <v-app-bar app clipped-left>
     <v-app-bar-nav-icon @click="drawer=!drawer"/>
       <v-icon class="mx-4">mdi-video</v-icon>
       <v-toolbar-title class="align-center">
         <span class="title">YouTube</span>
        </v-toolbar-title>
         <v-spacer/>
          <v-text-field class="mt-8" solo placeholder="Aramak için..." single-line append-icon="mdi-magnify" color="white" />
        <v-spacer/>
        <v-btn class="m1-0" icon>
          <v-icon>mdi-apps</v-icon>
        </v-btn>
        <v-btn class="ma-2" icon>
          <v-icon>mdi-bell</v-icon>
        </v-btn>
        <div>
          <v-menu v-model="menu" :close-on-content-click="false" :nudge-width="250" offset-x>
            <template v-slot:activator="{on}">
              <v-avatar size="40">
                <img v-on="on" src="https://icon-library.net/images/avatar-icon-images/avatar-icon-images-4.jpg"> 
              </v-avatar>
            </template>
            <v-card>
              <v-list>
                <v-list-item>
                  <v-list-item-avatar></v-list-item-avatar>
                  <v-list-item-content>
                    <v-list-item-title>Beytullah Öztürk</v-list-item-title>
                    <v-list-item-subtitle>Youtube User</v-list-item-subtitle>
                  </v-list-item-content>
                </v-list-item>
              </v-list>
              <v-divider/>
              <v-list>
                <v-list-item>
                  <v-list-item-action>
                    <v-icon>mdi-cog</v-icon>
                  </v-list-item-action>
                  <v-list-item-title>Ayarlar</v-list-item-title>
                </v-list-item>
                <v-list>
                  <v-list-item>
                    <v-list-item-action>
                      <v-switch v-model="theme" color="purple"/>
                    </v-list-item-action>
                    <v-list-item-title>Karanlık Tema</v-list-item-title>
                  </v-list-item>
                </v-list>
              </v-list>
              <v-cars-actions class="align-center">
                <v-spacer/>
                <v-btn color="primary" text @click="menu=false">Kapat</v-btn>
              </v-cars-actions>
            </v-card>
          </v-menu>
        </div>
   </v-app-bar>
  <!-- Header Stop -->
  <!-- Content Start -->
  <v-content>
    <v-container>
      <v-row class="mb-4">
        <v-col sm="6" md="4" lg="3" xl="2" v-for="(item,index) in 100" :key="index">
          <v-card>
            <v-img height="200px" :src="`https://picsum.photos/500/300?image=${(index)}`" :lazy-src="`https://picsum.photos/10/6?image=${(index+1)}`" />
            <v-card-title>Video {{index+1}} Başlık</v-card-title>
            <v-card-subtitle>Video {{index+1}} Açıklama</v-card-subtitle>
            <v-card-text class="text--primary">
              <div>Beytullah Öztürk<div>
              </div>152 kişi görüntüledi</div>
            </v-card-text>
            <v-divider/>
            <v-card-actions>
              <v-row align="center" justify="space-around">  
                <v-btn color="primary" text>izle</v-btn>
                <v-btn color="orange" text>Paylaş</v-btn>
              </v-row>
            </v-card-actions>
          </v-card>
        </v-col>      
      </v-row>
    </v-container> 
  </v-content>
  <!-- Content Stop -->
  </v-app>
</template>

<script>

export default {
  name: "App",

  data: () => ({
    items:[
      {icon:"mdi-trending-up", text:"Popüler İçerikler"},
      {icon:"mdi-youtube-subscription", text:"Takip Et"},
      {icon:"mdi-history", text:"Geçmiş"},
      {icon:"mdi-playlist-play", text:"Playlist Oynat"},
      {icon:"mdi-clock", text:"Daha sonra izle"},
    ],
    drawer:false,
    menu:false,
    theme:false
    
  }),
  watch:{
    theme:function(next){
      this.$vuetify.theme.dark=next
    }
  }
};
</script>
