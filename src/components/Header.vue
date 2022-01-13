<template>
  <div>
    <v-navigation-drawer v-model="drawer" fixed app>
      <v-list-item>
        <v-list-item-avatar>
          <v-img src="@/assets/logo.png"></v-img>
        </v-list-item-avatar>
        <v-list-item-content>
          <v-list-item-title> Admin </v-list-item-title>
          <v-list-item-subtitle> Admin Panel </v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>
      <v-divider />
      <v-list dense>
        <v-list-item-group color="teal darken-2">
          <v-list-item v-for="(item, i) in items" :key="i" :to="item.link" link>
            <v-list-item-icon>
              <v-icon v-text="item.icon"></v-icon>
            </v-list-item-icon>
            <v-list-item-content>
              <v-list-item-title v-text="item.title"></v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list-item-group>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar app color="primary" dark>
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
     
        <v-layout>
          <v-flex>
            <v-toolbar-title 
              >Application</v-toolbar-title
            >
          </v-flex>
        </v-layout>

        <v-row class="d-flex flex-row-reverse">
          <v-menu
            transition="slide-y-transition"
            bottom
            :nudge-width="250"
            :close-on-content-click="false"
          >
            <template v-slot:activator="{ on }">
              <v-btn flat icon class="mr-4" v-on="on">
                <v-icon large>mdi-account</v-icon>
              </v-btn>
            </template>
            <v-card class="cardBorderRadious">
              <v-list>
                <v-list-item-content class="pa-3">
                  <v-list-item-sub-title><b>Hello,</b></v-list-item-sub-title>
                  <v-list-item-title> Admin</v-list-item-title>
                </v-list-item-content>
              </v-list>
              <v-divider></v-divider>
              <v-card-actions>
                <v-spacer></v-spacer>
                <v-btn
                  text
                  title="Logout"
                  color="grey darken-1"
                  @click="logout"
                >
                  <v-icon class="mr-1">mdi-lock-open</v-icon>
                  Log out
                </v-btn>
              </v-card-actions>
            </v-card>
          </v-menu>
        </v-row>

    </v-app-bar>
  </div>
</template>

<script>
export default {
  name: "Header",
  data: () => ({
    drawer: false,

    items: [
      {
        title: "Home",
        icon: "mdi-home",
        href: "/",
        path: "/",
      },
    ],
    mini: true,
  }),
  created() {},
  mounted() {},
  methods: {},
};
</script>
<style>
.toolbar-color {
  background-color: #0d97f4 !important;
}

.icon-color .v-btn__content {
  color: #ffffff;
}

.icon-flipped {
  transform: scaleX(-1);
  -moz-transform: scaleX(-1);
  -webkit-transform: scaleX(-1);
  -ms-transform: scaleX(-1);
}
</style>