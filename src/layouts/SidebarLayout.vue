<template>
  <v-app id="sidebar">
    <v-navigation-drawer  v-model="drawer"
      app>
        <v-list-item>
          <v-list-item-content>
            <v-list-item-title class="text-h6">
              Carrinho
            </v-list-item-title>
          </v-list-item-content>
        </v-list-item>

        <v-divider></v-divider>

        <v-list
          dense
          nav
        >
          <v-list-item
            v-for="item in items"
            :key="item.title"
            :to="item.to"
            link
          >
            <v-list-item-icon>
              <v-icon>{{ item.icon }}</v-icon>
            </v-list-item-icon>

            <v-list-item-content>
              <v-list-item-title>{{ item.title }}</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list>
    </v-navigation-drawer>

    <v-app-bar app>
        <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

        <v-toolbar-title>Carrinho</v-toolbar-title>
        <v-col class="text-right">
          <div class="my-2">
            <v-btn color="warning" dark @click="Disconnect">Desconectar</v-btn>
          </div>
        </v-col>
    </v-app-bar>

    <v-main></v-main>
    <slot></slot>
  </v-app>
</template>

<script>
export default {
  data: () => ({
    drawer: false,
    items: [
      { title: 'Carrinho', icon: 'mdi-account-box-multiple', to: '/Cart' }
    ]
  }),
  methods: {
    Disconnect () {
      this.$router.push('/login')
    }
  }
}
</script>

