<template>
	<!--ChatList-->
	<div class="w-2/5 border-r border-orange-100">
		<div class="flex flex-col bg-orange-100 rounded-lg shadow-lg overflow-hidden h-screen">
			<div class=" bg-orange-300 p-4">
				<div class="flex flex-row items-center">
					<img src="/src/assets/img/Hassan.png" alt="User avatar" class="w-10 h-10 rounded-full mr-4">
					<span class="flex flex-col">
						<h2 class="text-xl font-bold text-gray-800">Your Chats List</h2>
						<h5 class="text-gray-800">@hasn_dev</h5>
					</span>
				</div>
			</div>
			<div class="flex-1 overflow-y-auto">
				<div class="flex flex-col p-4">
					<a @click="selectedConversationIndex = index" v-for="(conversation, index) in conversations"
						class="flex items-center text-gray-800 py-2 hover:bg-orange-200 rounded-lg mb-2 px-2">
						<img :src=conversation.img alt="User avatar" class="w-10 h-10 rounded-full mr-4">
						<div>
							<h3 class="text-lg font-medium">{{ conversation.title }}</h3>
							<p class="text-gray-600">{{ conversation.lastMessage }}</p>
						</div>
					</a>
				</div>
			</div>
		</div>
	</div>

	<!--ChatBubble-->
	<div class="w-3/5 flex-1 flex flex-col overflow-y-auto px-3 h-screen">
		<div v-if="currentConversation != null" class="flex flex-col px-2 mt-3 h-full w-full">
			<chat-bubble v-for="message in currentConversation.messages" :message="message"></chat-bubble>
		</div>
		<div v-else class="justify-center items-center h-full w-full">
			<div class="'flex flex-col my-4 items-start">
				<div class="max-w-xs px-4 py-2 rounded-lg bg-white text-gray-700">
					<p class="text-sm">Please select a conversation first</p>
				</div>
			</div>
		</div>
		<!-- Input area -->
		<div class="flex flex-row items-center justify-center border-t border-gray-300">
			<input type="text" placeholder="Type a message..."
				class="flex-1 px-4 py-2 rounded-lg bg-gray-200 focus:outline-none focus:shadow-outline-blue">
			<button class="bg-blue-500 hover:bg-blue-600 text-white px-4 py-2 rounded-lg ml-4">Send</button>
		</div>
	</div>
</template>

<script setup>
import { computed, ref } from "vue";
import ChatBubble from "@/components/ChatBubble.vue";
const props = defineProps({
	conversations: {
		type: [Array],
		required: true,
	}
})
const selectedConversationIndex = ref();
const currentConversation = computed(() => {
	return props.conversations[selectedConversationIndex.value];
});
</script>