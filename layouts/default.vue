<template>
  <v-app dark>
    <v-navigation-drawer
      v-model="drawer"
      fixed
      temporary
      app
      small
    >
      <v-list nav dense>
        <v-list-group
          v-for="(item, i) in items"
          :key="i"
          :prepend-icon="item.icon"
          sub-group
          no-action
        >
          <template v-slot:activator>
            <v-list-item-title>
              {{item.title}}
            </v-list-item-title>
          </template>
          <v-list-group
            v-for="(el, ind) in item.sub"
            :key="ind"
            sub-group
            no-action
          >
            <template v-slot:activator>
              <v-list-item-title>
                {{el.title}}
              </v-list-item-title>
            </template>
            <v-list-item
              v-for="(sm, index) in el.sub"
              :key="index"
              @click="$router.push(sm.to)"
              >
              <v-list-item-title>
                {{sm.title}}
              </v-list-item-title>
              <v-list-item-action>
                <fa :icon="['fas', sm.icon]" style="height: 16px; color: inherit;"/>
              </v-list-item-action>
            </v-list-item>
          </v-list-group>

        </v-list-group>
      </v-list>
      <template v-slot:append>
        <div class="pa-2">
          <v-btn block>Logout</v-btn>
        </div>
      </template>
    </v-navigation-drawer>
    <v-app-bar
      fixed
      app
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer"/>
      <v-toolbar-title>Octavues</v-toolbar-title>
      <v-spacer/>
      <v-btn
        icon
        @click.stop="rightDrawer = !rightDrawer"
      >
        <v-icon>mdi-menu</v-icon>
      </v-btn>
    </v-app-bar>
    <v-content>
      <v-container>
        <nuxt />
      </v-container>
    </v-content>
    <!-- <v-navigation-drawer
      v-model="rightDrawer"
      :right="right"
      temporary
      fixed
    >
      <v-list>
        <v-list-item @click.native="right = !right">
          <v-list-item-action>
            <v-icon light>
              mdi-repeat
            </v-icon>
          </v-list-item-action>
          <v-list-item-title>Switch drawer (click me)</v-list-item-title>
        </v-list-item>
      </v-list>
    </v-navigation-drawer> -->
    <v-footer
      :fixed="fixed"
      app
    >
      <span>&copy; 2019</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data () {
    return {
      drawer: false,
      fixed: false,
      items: [
        {
          title: "Мэдрэмж",
          icon: "mdi-apps",
          sub: [
            {
              title: "Quotes",
              sub: [
                {
                  icon: 'plus',
                  title: 'Add Quote',
                  to: '/medremj/quotes/add_quote'
                },{
                  icon: 'quote-left',
                  title: 'Quotes',
                  to: '/medremj/quotes'
                },{
                  icon: 'hashtag',
                  title: 'Hashtags',
                  to: '/medremj/quotes/hashtag'
                }
              ]
            },{
              title: "Musics",
              sub: [
                {
                  icon: 'plus',
                  title: 'Add Music',
                  to: '/medremj/musics/add_music'
                },
                {
                  icon: 'music',
                  title: 'Musics',
                  to: '/medremj/musics'
                },{
                  icon: 'hashtag',
                  title: 'Hashtags',
                  to: '/medremj/musics/hashtag'
                }
              ]
            },{
              title: "Requests",
              sub: [
                {
                  icon: "handshake",
                  title: "Collaboration",
                  to: "/medremj/requests/collaboration"
                },{
                  icon: "paper-plane",
                  title: "Music Request",
                  to: "/medremj/requests/music"
                },{
                  icon: "flag",
                  title: "Report Music",
                  to: "/medremj/requests/reportmusic"
                },{
                  icon: "flag",
                  title: "Report Quote",
                  to: "/medremj/requests/reportquote"
                },{
                  icon: "flag",
                  title: "Report music channel",
                  to: "/medremj/requests/reportchannel"
                },{
                  icon: "flag",
                  title: "Report Hashtag",
                  to: "/medremj/requests/reporthashtag"
                },
              ]
            },
          ]
        }
      ],
      right: true,
      rightDrawer: false,
      title: 'Vuetify.js'
    }
  }
}
</script>
