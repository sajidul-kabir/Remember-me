<template>
  <base-dialog
    v-if="isInvalid"
    title="Invalid Input"
    @close-modal="confirmError"
  >
    <template #default>
      <p>Fill up all the inputs</p>
      <p>
        Please check all the inputs and make sure you inputted all the fields
      </p>
    </template>
    <template #actions>
      <base-button @click="confirmError">Okay</base-button>
    </template>
  </base-dialog>
  <base-card>
    <form @submit.prevent="collectInputs()">
      <div class="form-control">
        <label for="title">Title</label>
        <input id="title" name="title" type="text" v-model="userInput.title" />
      </div>
      <div class="form-control">
        <label for="description">Description</label>
        <textarea
          name="description"
          id="description"
          rows="3"
          v-model="userInput.description"
        ></textarea>
      </div>
      <div class="form-control">
        <label for="link">Link</label>
        <input id="link" name="link" type="url" v-model="userInput.link" />
      </div>
      <div>
        <base-button type="submit">Add Resource</base-button>
      </div>
    </form>
  </base-card>
</template>

<script>
import BaseButton from '../UI/BaseButton.vue';
import BaseCard from '../UI/BaseCard.vue';
import BaseDialog from '../UI/BaseDialog.vue';
export default {
  components: { BaseButton, BaseCard, BaseDialog },
  emits: ['user-input'],
  // emits: ['eve-nting'],
  data() {
    return {
      isInvalid: false,
      userInput: {
        id: '',
        title: '',
        description: '',
        link: '',
      },
    };
  },
  methods: {
    collectInputs() {
      if (
        this.userInput.title === '' ||
        this.userInput.description === '' ||
        this.userInput.link === ''
      ) {
        this.isInvalid = true;
        return;
      }
      this.userInput.id = Date.now();
      this.$emit('user-input', this.userInput);
      //this.$emit('eve-nting', 'riga');
    },
    confirmError() {
      this.isInvalid = false;
    },
  },
};
</script>

<style scoped>
label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15rem;
  border: 1px solid #ccc;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}

.form-control {
  margin: 1rem 0;
}
</style>
