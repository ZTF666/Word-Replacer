<template>
  <v-app :dark="setTheme">
    <v-app-bar
      :clipped-left="clipped"
      fixed
      app
      color="primary secondary--text"
      class="hidden-xs-only"
    >
      <v-img
        alt="Vuetify Logo"
        class="shrink mr-2 img"
        contain
        :src="logo"
        transition="scale-transition"
        width="40"
      />
      <v-toolbar-title v-text="title" />

      <v-btn text>
        <v-switch v-model="goDark" color="dark" :label="icon" class="mt-5"></v-switch>
      </v-btn>
      <v-spacer />
      <v-btn icon class="secondary--text"  href="https://github.com/ZTF666/Word-Replacer" target="_blank"><v-icon>mdi-github</v-icon></v-btn>
    </v-app-bar>

    <!-- mobile app bar -->
    <v-app-bar :clipped-left="clipped" fixed app color="primary" class="hidden-sm-and-up">
      <v-img
        alt="Vuetify Logo"
        class="shrink mr-2 img"
        contain
        :src="logo"
        transition="scale-transition"
        width="40"
      />
      <v-toolbar-title v-text="title" class="secondary--text" />
      <v-spacer></v-spacer>
      <v-menu left bottom>
        <template v-slot:activator="{ on, attrs }">
          <v-btn icon v-bind="attrs" v-on="on">
            <v-icon>mdi-dots-vertical</v-icon>
          </v-btn>
        </template>

        <v-list>
          <!-- <v-list-item> -->
          <v-list-item-content>
            <v-btn text>
              <v-switch v-model="goDark" color="secondary" :label="icon" class="mb-5"></v-switch>
            </v-btn>

            <!-- <v-spacer></v-spacer> -->
            <v-btn icon class="secondary--text" href="https://github.com/ZTF666/Word-Replacer" target="_blank"><i icon>mdi-github </i></v-btn>
            
          </v-list-item-content>

          <!-- </v-list-item> -->
        </v-list>
      </v-menu>
    </v-app-bar>

    <!-- end mobile app bar -->

    <v-main :class="BgCol">
      <v-container>
        <nuxt />
      </v-container>
    </v-main>

    <v-footer :absolute="!fixed" app color="primary secondary--text">
      <span>&copy; {{ new Date().getFullYear() }}</span>
      <v-spacer></v-spacer>
      <span>
        Made with ❤️ by
        <a
          href="https://ztfportfolio.web.app/"
          target="blank"
          class="pinkish--text zztop"
        >
          <strong>ZTF</strong>
        </a>
      </span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
 head: {
    title: 'Home page',
    meta: [
      {
        hid: 'Word Replacer',
        name: 'Word Replacer',
        content: 'Alter your text and change a recurring word in it by anything else you wish',
      },
    ],
  },
  data() {
    return {
      icon: '🌚',
      goDark: true,
      BgCol: 'bg',
      logo: require('../assets/9.png'),
      //
      clipped: false,
      fixed: false,
      title: 'Word ♻️ Replacer',
    }
  },
  computed: {
    setTheme() {
      if (this.goDark === true) {
        this.$vuetify.theme.dark = true
        this.icon = '🌚'
        this.BgCol = 'bg'
      } else {
        this.$vuetify.theme.dark = false
        this.icon = '🌞'
        this.BgCol = 'bgl'
      }
    },
  },
}
</script>
<style lang="scss">
.img {
  border-radius: 100px;
}
.bg {
  background-color: #000000;

}
.bgl {

  background-color: #a3ccce;

}
.zztop {
  text-decoration: none;
}
</style>