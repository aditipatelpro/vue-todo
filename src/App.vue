<template lang="pug">
  v-app(id="inspire")
    v-navigation-drawer(
      v-model="drawer"
      app
    )
      v-list-item
        v-list-item-content
          v-list-item-title(class="text-h6") Simple Todo

      v-divider

      v-list(
        dense
        nav
      )
        v-list-item(
          v-for="item in items"
          :key="item.title"
          link
        )
          v-list-item-icon
            v-icon {{ item.icon }}

          v-list-item-content
            v-list-item-title {{ item.title }}

    v-app-bar(app)
      v-app-bar-nav-icon(@click="drawer = !drawer")
      v-toolbar-title Application

    v-main
      router-view
</template>

<script>
export default {
  data: () => ({
    drawer: null,
    items: [
      { title: 'Todo', icon: 'mdi-format-list-checks' },
      { title: 'About', icon: 'mdi-help-box' },
    ],
  }),
};
</script>
