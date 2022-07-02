<template>
  <the-header title="RememberMe"></the-header>
  <stored-resources @selected-tab="changeTab"></stored-resources>
  <ul v-if="selectedTab === 'stored-resources'">
    <resource-item
      v-for="resource in resources"
      :key="resource.id"
      :title="resource.title"
      :description="resource.description"
      :link="resource.link"
    ></resource-item>
  </ul>
  <add-resources v-else></add-resources>
</template>

<script>
import ResourceItem from './components/learning-resources/ResourceItem.vue';
import TheHeader from './components/layouts/TheHeader.vue';
import StoredResources from './components/learning-resources/ToggleResources.vue';
import AddResources from './components/learning-resources/AddResources.vue';

export default {
  components: {
    ResourceItem,
    TheHeader,
    StoredResources,
    AddResources,
  },
  data() {
    return {
      selectedTab: 'stored-resources',
      resources: [
        {
          id: 1,
          title: 'Official guide for Vue',
          description: 'The official Vue.js documentation',
          link: 'https://vuejs.org/',
        },
        {
          id: 2,
          title: 'Google',
          description: 'Learn to google',
          link: 'https://google.com/',
        },
      ],
    };
  },
  methods: {
    changeTab(tab) {
      this.selectedTab = tab;
    },
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

* {
  box-sizing: border-box;
}

html {
  font-family: 'Roboto', sans-serif;
}

body {
  margin: 0;
}
ul {
  list-style: none;
  margin: 0;
  padding: 0;
  margin: auto;
  max-width: 40rem;
}
</style>
