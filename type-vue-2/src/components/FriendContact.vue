<script lang="ts">
import { defineComponent } from 'vue';
import { defineProps } from 'vue';

export default defineComponent({

  props: {
    id: {
      type: String,
      require: true
    },
    isFavorite: {
      type: Boolean,
      default: false,
      require: true,
    },
    name: {
      type: String,
      required: true
    },
    phone: {
      type: String,
    },
    email: {
      type: String,
      required: true
    }
  },

  data() {
    return {
      isVisible: false,
    };
  },

  methods: {
    toggleDetails() {
      this.isVisible = !this.isVisible;
    },
    changeFavoriteValue() {
      // Permite hacer un evento personalizado que puedes ejecutar desde el componente padre. Recibe como primer parametro el
      // nombre del evento y como adicionales los datos que devolvera.
      this.$emit('change-favorite', this.id); //convecion: kebap-case
    },
  },
});

</script>

<template>
  <li>
    <h2>{{ name }} {{ isFavorite ? '(Favorite)' : '' }}</h2>
    <button @click="toggleDetails">{{ isVisible ? 'Hide' : 'Show' }} Details</button>
    <button @click="changeFavoriteValue">Change Favorite Prop</button>
    <ul v-if="isVisible">
      <li>
        <strong>Phone:</strong>
        {{ phone }}
      </li>
      <li>
        <strong>Email:</strong>
        {{ email }}
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
