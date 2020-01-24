<template>
  <v-app>
    <v-navigation-drawer
      v-model="drawer"
      app
      clipped
      mobile-break-point="0"
    >
      <v-list dense>
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-navigation-drawer
      v-model="authorDrawer"
      app
      right
      clipped
      mini-variant
      temporary
      mobile-break-point="0"
    >
      <v-list>
        <v-list-item>
          <v-list-item-action>
            <v-icon light>
              mdi-repeat
            </v-icon>
          </v-list-item-action>
          <v-list-item-title>Switch drawer (click me)</v-list-item-title>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar
      app
      color="primary"
      dark
      clipped-left
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <!-- <v-btn
        @click.stop="miniVariant = !miniVariant"
        icon
      >
        <v-icon>mdi-{{ `chevron-${miniVariant ? 'right' : 'left'}` }}</v-icon>
      </v-btn>
      <v-btn
        @click.stop="clipped = !clipped"
        icon
      >
        <v-icon>mdi-application</v-icon>
      </v-btn>
      <v-btn
        @click.stop="fixed = !fixed"
        icon
      >
        <v-icon>mdi-minus</v-icon>
      </v-btn> -->
      <v-toolbar-title v-text="title" />
      <v-spacer />
      <!-- <v-hover v-slot:default="{ hover }">
        <v-btn
          @click.stop="authorDrawer = !authorDrawer"
          :elevation="hover ? 12 : 2"
          icon
        >
          <v-avatar>
            <v-img
              v-bind:src="authorImage"
              alt="author"
            />
          </v-avatar>
        </v-btn>
      </v-hover> -->

      <v-speed-dial
        v-model="fab"
        direction="bottom"
        open-on-hover
      >
        <v-btn
          slot="activator"
          v-model="fab"
          icon
          dark
        >
          <v-avatar>
            <v-img
              v-bind:src="authorImage"
              alt="author"
            />
          </v-avatar>
        </v-btn>

        <v-btn
          fab
          dark
          small
        >
          <v-avatar>
            <v-img
              v-bind:src="authorImage"
              alt="author"
            />
          </v-avatar>
        </v-btn>

        <v-btn
          fab
          dark
          small
        >
          <v-icon>add</v-icon>
        </v-btn>
      </v-speed-dial>
    </v-app-bar>

    <v-content>
      <v-container fluid>
        <nuxt />
      </v-container>
    </v-content>

    <v-footer app>
      <span>&copy; {{ copyright }}</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data () {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: 'mdi-apps',
          title: 'Welcome',
          to: '/'
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'Inspire',
          to: '/inspire'
        }
      ],
      miniVariant: false,
      authorDrawer: false,
      title: 'WEAL | web engineer action log',
      authorImage: 'https://firebasestorage.googleapis.com/v0/b/kbsh-vue-blog.appspot.com/o/images%2Fauthor.jpeg?alt=media&token=87dfc57d-264c-4d2a-96b3-d27c99084043',
      copyright: '2019 kbsh'
    }
  }
}
</script>
