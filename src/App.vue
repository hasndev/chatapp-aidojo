<template>
  <div class="flex h-screen bg-gray-100 w-full">
    <chatList :conversations="conversations"></chatList>
  </div>
</template>

<script setup>
import chatList from '@/components/ChatList.vue' //2:07:02
import { ref } from 'vue';

const conversations = ref([]);
conversations.value.push({
  title: "Chat With Ali",
  messages: [
    {
      outgoing: false,
      text: "Hellow, Ali",
      username: "hdrm147"
    },
    {
      outgoing: true,
      text: "Hello, Hassan!",
      username: "azeez"
    },
  ],
  lastMessage: "Hello, Hassan!",
  img: "/src/assets/img/ali-user-1.jpg"
}),
  conversations.value.push({
    title: "Chat With Luma",
    messages: [
      {
        outgoing: false,
        text: "Learn JS",
        username: "hdrm147"
      },
      {
        outgoing: true,
        text: "Yes I'll do that",
        username: "azeez"
      },
    ],
    lastMessage: "Yes I'll do that",
    img: "/src/assets/img/luma-user-2.jpg"
  }),
  conversations.value.push({
    title: "Chat With Karrar",
    messages: [
      {
        outgoing: false,
        text: "How are You?",
        username: "hdrm147"
      },
      {
        outgoing: true,
        text: "I'm fine ,thanks.",
        username: "azeez"
      },
    ],
    lastMessage: "I'm fine ,thanks.",
    img: "/src/assets/img/karrar-user-3.jpg"
  })
</script>
