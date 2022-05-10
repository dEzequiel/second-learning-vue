<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  data() {
    return {
      isVisible: false,
      friend: {
        id: "manuel",
        name: "Manuel Lorenz",
        phone: "0123 45678 90",
        email: "manuel@localhost.com",
      }
    };
  },

  methods: {
    toggleDetails() {
      this.isVisible = !this.isVisible;
    }
  }
});

</script>

<template>
  <li>
    <h2>{{ friend.name }}</h2>
    <button @click="toggleDetails">{{ isVisible ? 'Hide' : 'Show' }} Details</button>
    <ul v-if="isVisible">
      <li>
        <strong>Phone:</strong>
        {{ friend.phone }}
      </li>
      <li>
        <strong>Email:</strong>
        {{ friend.email }}
      </li>
    </ul>
  </li>
</template>

<style scoped>
a {
  color: #42b983;
}

label {
  margin: 0 0.5em;
  font-weight: bold;
}

code {
  background-color: #eee;
  padding: 2px 4px;
  border-radius: 4px;
  color: #304455;
}
</style>
