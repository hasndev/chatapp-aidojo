<template>
	<div :class="{ 'flex flex-col my-4 items-start': message.outgoing, 'items-end': message.outgoing }">
		<div
			:class="{ 'max-w-xs px-4 py-2 rounded-lg text-gray-700 bg-orange-300': !message.outgoing, 'max-w-xs px-4 py-2 rounded-lg text-gray-700 bg-blue-300': message.outgoing }">
			<p class="text-sm">{{ message.text }}</p>
		</div>
		<div class="text-gray-600 text-xs mt-1">{{ message.username }}</div>
	</div>
</template>

<script setup>

const props = defineProps(["message"]);

</script>