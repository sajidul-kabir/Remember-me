<template>
  <base-card>
    <base-button
      @click="setSelectedTab('stored-resources')"
      :mode="checkbutton1Mode"
      >Stored Resources</base-button
    >
    <base-button
      @click="setSelectedTab('add-resources')"
      :mode="checkbutton2Mode"
      >Add Resources</base-button
    >
  </base-card>
</template>

<script>
import BaseButton from '../UI/BaseButton.vue';
import BaseCard from '../UI/BaseCard.vue';
export default {
  components: {
    BaseButton,
    BaseCard,
  },
  emits: ['selected-tab'],
  props: ['dummy'],
  data() {
    return {
      selectedTab: 'stored-resources',
    };
  },
  computed: {
    checkbutton1Mode() {
      if (
        this.selectedTab === 'stored-resources' ||
        this.dummy === 'stored-resources'
      ) {
        return 'null';
      } else {
        return 'flat';
      }
    },
    checkbutton2Mode() {
      if (this.selectedTab === 'add-resources' && this.dummy === '') {
        return 'null';
      } else {
        return 'flat';
      }
    },
  },
  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
      this.$emit('selected-tab', tab);
    },
  },
};
</script>
