<template>
  <q-page class="flex flex-center">
    <div style="width: 100%">
      <q-scroll-area
        style="height: 540px"
        :thumb-style="{
          borderRadius: '5px',
          background: '#26A69A',
          width: '4px',
          opacity: 1,
        }"
      >
        <ChatMessage v-for="chat in chats" :key="chat.key" :chat="chat" />
      </q-scroll-area>
    </div>

    <q-footer bordered class="bg-primary text-white">
      <MainFooter />
    </q-footer>
  </q-page>
</template>

<script setup>
import ChatMessage from "../components/ChatMessage.vue";
import { useRoomStore } from "../stores/room";
import { computed } from "vue";
import MainFooter from "../components/MainFooter.vue";

const store = useRoomStore();
const chats = computed(() => store.currentChatList);
</script>

<style lang="scss">
.my-emoji {
  vertical-align: middle;
  height: 2em;
  width: 2em;
}
</style>
