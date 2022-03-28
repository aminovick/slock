<template lang="">
  <div>
    <div>
      <input
        placeholder="Entrer un message"
        id="name"
        type="text"
        v-model="message"
      />
      <button
        class="button-primary"
        @click="sendMessage"
        :disabled="message === ''"
      >
        Envoyer
      </button>
    </div>
  </div>
</template>
<script setup>
import { ref } from "vue";
// State
const message = ref("");

// Methods
function sendMessage() {
  window.alert(message.value);
  message.value = ""; // Empty the text input
}
</script>

<style lang="scss">
@import "@/assets/base.scss";
.compose {
  display: flex;
  gap: 1rem;
  padding: 1rem;
  background-color: var(--color-background-2);

  input {
    flex: 1 1 0;
  }
}
</style>
