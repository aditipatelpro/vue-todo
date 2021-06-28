<template lang="pug">
  v-app(id="inspire")
    v-navigation-drawer(
      v-model="drawer"
      app
    )
      v-list-item
        v-list-item-content
          v-list-item-title(class="text-h6") Simple Todo
          v-list-item-subtitle Because you got todo!

      v-divider

      v-list(
        dense
        nav
      )
        v-list-item(
          v-for="item in items"
          :key="item.title"
          link
          :to="item.url"
        )
          v-list-item-icon
            v-icon {{ item.icon }}

          v-list-item-content
            v-list-item-title {{ item.title }}

    v-app-bar(
      app
      color="primary"
      dark
      src="waves.jpg"
      prominent
    )
      template(v-slot:img="{ props }")
        v-img(
          v-bind="props"
          gradient="to top right, rgba(19,84,122,.5), rgba(128,208,199,.8)"
        )
      v-app-bar-nav-icon(@click="drawer = !drawer")
      v-toolbar-title Simple Todo

    v-main
      router-view
</template>

<script>
export default {
  data: () => ({
    drawer: null,
    items: [
      { icon: 'mdi-format-list-checks', title: 'Todo', url: '/' },
      { icon: 'mdi-help-box', title: 'About', url: '/about' },
    ],
  }),
};
</script>
