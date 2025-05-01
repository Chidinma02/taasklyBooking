<template>
	<div
		class="flex flex-col sm:flex-row items-start sm:items-center items-center gap-5 w-full border-b border-b-[#E9E9E9] pb-8 mb-6">
		<input ref="fileInput" class="hidden" type="file" accept="image/jpeg,image/png" @change="handleFileInputChange">
		<div class="rounded-lg flex items-center justify-center border overflow-hidden"
			:style="`width:${size}; height:${size}`">
			<img v-if="photoUrl" :src="photoUrl" class="h-full w-full object-cover" alt="">
			<img v-else src="/filler.svg" class="h-full w-full object-cover" alt="">
		</div>

		<div class="flex flex-col gap-2 mt-4 sm:mt-0">
			<p class="text-sm font-semibold text-gray-800 text-[#101928]">Profile Photo</p>
			<p class=" text-sm font-semibold text-gray-500">Add a profile image</p>
			<div class="flex gap-3 mt-1">
				<button
					class="px-3 py-1 text-sm border border-[#CFD7FF] rounded-md text-blue-600 hover:bg-blue-50 text-[#000E84]">
					Remove Image
				</button>
				<button
					class="px-3 py-1 text-sm border border-[#CFD7FF] rounded-md text-blue-600 hover:bg-blue-50 text-[#000E84]">
					Upload Image
				</button>
			</div>

		</div>
		<!-- <button class="btn-primary w-auto px-5" :disabled="loading" type="button" @click="selectPhoto">
			<span v-if="!loading">{{ btnName }}</span>
			<span v-else class="flex items-center gap-2.5">
				<Spinner size="16px" />
				<span v-if="loading">Uploading..</span>
				<span v-if="percentage"> {{ percentage }}%</span>
			</span>
		</button> -->
	</div>
</template>

<script setup lang="ts">
import { uploadFirebasetorage } from '@/firebase/storage'

const emit = defineEmits(['update'])
const props = defineProps({
	photoUrl: {
		default: '',
		type: String,
		required: true
	},
	folderName: {
		default: '',
		type: String,
		required: true
	},
	btnName: {
		default: 'Change Photo',
		type: String,
		required: false
	},
	size: {
		default: '150px',
		type: String,
		required: false
	}
})
const file = ref() as Ref<File>
const fileInput = ref() as Ref<HTMLInputElement>
const { percentage, downloadURL, upload, loading } = uploadFirebasetorage()
const handleFileInputChange = () => {
	if (fileInput.value.files?.[0]) {
		file.value = fileInput.value.files?.[0] as File
		upload(props.folderName, file)
	}
}

const selectPhoto = () => {
	fileInput.value.click()
}

watch(downloadURL, () => {
	emit('update', downloadURL.value)
})
</script>
