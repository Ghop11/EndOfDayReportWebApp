<template>
  <v-app>
    <v-app-bar app>
      <v-toolbar-title class="headline text-uppercase">
        <span>End Of Day </span>
        <span class="font-weight-light">Reports</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
<!--        removing the button since I moved it back to a single pge app-->
<!--        <router-link to="/"><v-btn><span class="mr-2">New Report</span></v-btn></router-link>-->
<!--        <v-btn @click="this.goHome()"><span class="mr-2">New Report</span></v-btn>-->
    </v-app-bar>
    <v-content>
      <center><v-img id="logo" src='./assets/1.png' max-width="250px"></v-img></center>
      <router-view></router-view>
    </v-content>
  </v-app>
</template>



<script>

export default {
  name: 'App',
  components: {
  },
  data: () => ({
    //
      methods: {
          goHome: function () {
              this.$router.push('/')
          }
      }
  }),
};
</script>
