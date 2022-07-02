<template>
  <ul>
    <li v-for="resource in resources" :key="resource.id">
      {{ resource.title }}
      {{ resource.description }}
    </li>
  </ul>
</template>

<script>
export default {
  data() {
    return {
      resources: [
        {
          id: 1,
          title: 'Official guide',
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
};
</script>

<style></style>
