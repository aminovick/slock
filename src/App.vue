<template lang="">
  <div class="room">
    <div class="messages" v-html="messageOutput"></div>
    <div class="compose">
      <input
        placeholder="Entrer un message"
        id="name"
        type="text"
        v-model="message"
      />
      <button
        class="button-primary"
        @click="sendMessage"
        :disabled="isButtonDisabled"
      >
        Envoyer
      </button>
    </div>
  </div>
</template>
<script setup>
import { ref,computed, reactive } from "vue";
// State
const message = ref("");

const messageText=reactive([]);

const isButtonDisabled = computed(() => message.value.length === 0)
// Methods
function sendMessage() {
 messageText.push(message.value);
 message.value = ""; // Empty the text input
}

const messageOutput=computed(()=>{
 
  const styledMessages = messageText.map(m => `<p><strong>Amine</strong> ${new Intl.DateTimeFormat('en-GB', { dateStyle: 'full', timeStyle: 'long' }).format(new Date())}<br>${m}</p>`)
  return styledMessages.join('<br>')

})


</script>

<style lang="scss">
@import './assets/base.scss';
.room{
  display: flex;
  flex-direction: column;
}
.messages{
  flex: 1 1 0;
      padding: 1rem;
    overflow: scroll;
}
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
