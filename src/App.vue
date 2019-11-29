<template>
  <v-app id="keep">
    <v-app-bar
      app
      clipped-left
      color="grey lighten-3"
    >
      <v-app-bar-nav-icon @click="drawer = !drawer"><v-icon>fa-bars</v-icon></v-app-bar-nav-icon>
      <span class="title ml-3 mr-5">Google&nbsp;<span class="font-weight-light">Keep</span></span>
      <v-text-field
        solo-inverted
        flat
        hide-details
        label="Search"
        prepend-inner-icon="search"
      />

      <v-spacer />
    </v-app-bar>

    <v-navigation-drawer
      v-model="drawer"
      app
      clipped
      color="blue darken-1"
    >
      <v-list
        dense
        class="blue darken-1"
      >
        <template v-for="(item, i) in items">
          <v-row
            v-if="item.heading"
            :key="i"
            align="center"
          >
            <v-col cols="6">
              <v-subheader>
                {{ item.heading }}
              </v-subheader>
            </v-col>
            <v-col
              cols="6"
              class="text-right"
            >
              <v-btn
                small
                text
              >edit</v-btn>
            </v-col>
          </v-row>
          <v-divider
            v-else-if="item.divider"
            :key="i"
            dark
            class="my-4"
          />
          <v-list-item
            v-else
            :key="i"
            link
          >
            <v-list-item-action>
              <v-icon dark>{{ item.icon }}</v-icon>
            </v-list-item-action>
            <v-list-item-content>
              <v-list-item-title class="white--text">
                {{ item.text }}
              </v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </template>
      </v-list>
    </v-navigation-drawer>

    <v-content>
      <v-container
        fluid
        class="grey lighten-4 fill-height"
      >
        <v-row
          justify="center"
          align="center"
        >
          <v-col class="shrink">
            <HelloWorld/>
          </v-col>
        </v-row>
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
import HelloWorld from './components/HelloWorld';
  export default {
    props: {
      source: String,
    },
    data: () => ({
      drawer: null,
      items: [
        { icon: 'lightbulb_outline', text: 'Notes' },
        { icon: 'touch_app', text: 'Reminders' },
        { divider: true },
        { heading: 'Labels' },
        { icon: 'add', text: 'Create new label' },
        { divider: true },
        { icon: 'archive', text: 'Archive' },
        { icon: 'delete', text: 'Trash' },
        { divider: true },
        { icon: 'settings', text: 'Settings' },
        { icon: 'chat_bubble', text: 'Trash' },
        { icon: 'help', text: 'Help' },
        { icon: 'phonelink', text: 'App downloads' },
        { icon: 'keyboard', text: 'Keyboard shortcuts' },
      ],
    }),
    components: {
    HelloWorld,
  },
  }
</script>

<style>
#keep .v-navigation-drawer__border {
  display: none
}
</style>