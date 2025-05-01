<template>
	<div class="settings-layout flex flex-col md:flex-row gap-4">
		<aside class="sidebar   px-4 py-6">
			<ul>
				<li v-for="item in tabs" :key="item.name" :class="{ active: currentTab === item.name }"
					@click="currentTab = item.name">
					{{ item.label }}
				</li>
			</ul>
		</aside>

		<!-- Content Area -->
		<section class="content-area  px-6 py-8  lg:mr-[17.5rem]">
			<component :is=" currentTabComponent" />
		</section>

		<!-- <p>perm</p>
		<main class="flex flex-col gap-4 px-5 mt-8">
			<div class="flex flex-col md:flex-row items-start md:items-center gap-6 justify-between">
				<ProfilePhoto v-if="userProfile" :photo-url="userProfile.photo_url"
					:folder-name="`bookings/users/profile/${user_id}`" @update="updatePhoto" />
			</div>



			<span class="flex items-center justify-between my-4 mt-12">
				<h1 class="page-title">
					Personalize
				</h1>
				<div>
					<button v-if="isDisabled" class="btn-primary" @click="isDisabled = false">
						Edit Profile
					</button>
					<button v-else class=" font-medium btn-primary" :disabled="profileLoading" @click="update">
						<span v-if="!profileLoading">Save changes</span>
						<Spinner v-else />
					</button>
				</div>
			</span>

			<section id="uneditable" class="grid sm:grid-cols-2 md:grid-cols-3 mt-8 gap-x-4 gap-y-8">
				<div class="field">
					<label>
						Full Name
					</label>
					<input id="first_name" v-model="userProfileForm.name.value" type="text" class="input-field"
						:disabled="isDisabled" required>
				</div>

				<div class="field">
					<label>
						email
					</label>
					<input id="email" v-model="userProfileForm.email.value" type="text" class="input-field"
						:disabled="true" required>
				</div>
				<div class="field">
					<label>
						username
					</label>
					<input id="username" v-model="userProfileForm.username.value" type="text" class="input-field"
						:disabled="true" required>
				</div>
				<div class="field">
					<label>
						Phone
					</label>
					<input id="phone" v-model="userProfileForm.phone.value" type="text" class="input-field"
						:disabled="true" required>
				</div>
				<div class="field">
					<label>
						Bio
					</label>
					<textarea v-model="userProfileForm.bio.value" placeholder="A short introduction about yourself"
						rows="4" class="input-textarea" required :disabled="isDisabled" />
				</div>
			</section>
		</main> -->
	</div>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue'
import ProfileTab from './ProfileTab.vue'
import SecurityTab from './SecurityTab.vue'
import NotificationsTab from './NotificationsTab.vue'
import DataPrivacyTab from './dataandprivacy.vue'
import { usePageHeader } from '@/composables/utils/header'
import { useUser } from '@/composables/auth/user'
import { useUpdateUserProfile } from '@/composables/auth/profile/edit'


const { user, id: user_id, userProfile } = useUser()
const { isDisabled, loading: profileLoading, populateData, update, updatePhoto, userProfileForm } = useUpdateUserProfile()

const tabs = [
	{ name: 'Profile', label: 'Profile' },
	{ name: 'Security', label: 'Security' },
	{ name: 'NotificationsTab', label: 'NotificationsTab' },

	{ name: 'DataPrivacy', label: 'Data & Privacy' }

]

const currentTab = ref('Profile')

const currentTabComponent = computed(() => {
	switch (currentTab.value) {
		case 'Profile':
			return ProfileTab
		// These can be added as you create the components
		case 'Security': return SecurityTab
		case 'NotificationsTab': return NotificationsTab
		case 'DataPrivacy': return DataPrivacyTab
		default:
			return ProfileTab
	}
})


populateData()

definePageMeta({
	layout: 'dashboard',
	middleware: ['is-authenticated', () => {
		usePageHeader().setPageHeader({
			title: 'Settings',
			description: 'Manage your bookings account settings here',
			btnText: 'Add Booking Type',
			shouldShowFab: false,
			shouldShowTab: false

		})
	}]
})
</script>

<style scoped>
.sidebar {
	width: 220px;
	padding: 2rem;


}

.sidebar ul {
	list-style: none;
	padding: 0;
}

.sidebar li {
	padding: 0.8rem 1rem;
	cursor: pointer;
	color: #6b7280;
	border-left: 3px solid transparent;
	transition: all 0.2s ease-in-out;
}

.sidebar li.active {
	color: #111827;
	font-weight: 600;
	border-left-color: #6366f1;

}

.content-area {
	flex: 1;
	padding: 2rem;
	background-color: #fff;
}
</style>
