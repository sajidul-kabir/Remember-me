<template>
  <the-header title="RememberMe"></the-header>
  <toggle-resources :dummy="dummy" @selected-tab="changeTab"></toggle-resources>
  <ul v-if="selectedTab === 'stored-resources'">
    <resource-item
      v-for="resource in resources"
      :key="resource.id"
      :id="resource.id"
      :title="resource.title"
      :description="resource.description"
      :link="resource.link"
      @delete-resource="deleteResource"
    ></resource-item>
  </ul>
  <add-resources v-else @user-input="addResource($event)"></add-resources>
</template>

<script>
import ResourceItem from './components/learning-resources/ResourceItem.vue';
import TheHeader from './components/layouts/TheHeader.vue';
import ToggleResources from './components/learning-resources/ToggleResources.vue';
import AddResources from './components/learning-resources/AddResources.vue';

export default {
  components: {
    ResourceItem,
    TheHeader,
    ToggleResources,
    AddResources,
  },

  data() {
    return {
      selectedTab: 'stored-resources',
      dummy: '',
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
      this.dummy = '';
    },
    addResource(resource) {
      this.resources.push(resource);
      this.selectedTab = 'stored-resources';
      this.dummy = 'stored-resources';
    },
    deleteResource(id) {
      let index = 0;
      this.resources.every(function (resource) {
        //console.log(index);
        if (id === resource.id) {
          return false;
        }
        index++;
        return true;
      });
      console.log(index);
      this.resources.splice(index, 1);
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
