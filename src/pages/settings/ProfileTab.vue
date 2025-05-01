<template>
    <div>
        <main class="flex flex-col gap-4 px-5 mt-4">
            <p class="page-title">Profile Information</p>
            <div class="flex flex-col md:flex-row items-start md:items-center gap-6 justify-between mt-5">
                <ProfilePhoto v-if="userProfile" :photo-url="userProfile.photo_url"
                    :folder-name="`bookings/users/profile/${user_id}`" @update="updatePhoto" />
            </div>
            <span class="flex items-center justify-between my-4 mt-6">
                <div>
                    <h1 class="text-lg font-semibold text-gray-800 text-[#101928]">
                        Personal Information
                    </h1>
                    <p class="text-[#0009448A] font-semibold">Update your personal details here.</p>
                </div>

                <!-- <div>
                    <button v-if="isDisabled" class="btn-primary" @click="isDisabled = false">
                        Edit Profile
                    </button>
                    <button v-else class=" font-medium btn-primary" :disabled="profileLoading" @click="update">
                        <span v-if="!profileLoading">Save changes</span>
                        <Spinner v-else />
                    </button>
                </div> -->
            </span>

            <!-- <section id="uneditable" class="grid sm:grid-cols-2 md:grid-cols-3 mt-8 gap-x-4 gap-y-8"> -->
            <section id="uneditable" class="grid grid-cols-12  mt-6 gap-x-4 gap-y-8  border-b border-b-[#E9E9E9]">
                <div class="field col-span-12">
                    <label>
                        Full Name
                    </label>
                    <input id="first_name" v-model="userProfileForm.name.value" type="text" placeholder="Okubote Eniola"
                        class="w-full border border-[#CFD7FF] rounded-md px-4 py-2 focus:outline-none focus:ring-2 focus:ring-[#CFD7FF]  border-[1px] "
                        required>
                </div>
                <div class="field col-span-12">
                    <label>
                        Email Address
                    </label>
                    <input id="email" v-model="userProfileForm.email.value" type="text"
                        class="w-full border border-[#CFD7FF] rounded-md px-4 py-2 focus:outline-none focus:ring-2 focus:ring-[#CFD7FF]"
                        placeholder="Enter Email" required>
                </div>
                <!-- <div class="field col-span-12 ">
                    <label>
                        username
                    </label>
                    <input id="username" v-model="userProfileForm.username.value" type="text" class="input-field"
                        :disabled="true" required>
                </div> -->
                <div class="field col-span-12">
                    <label>
                        Phone Number (whatsapp preferably)
                    </label>
                    <PhoneInput v-model="userProfileForm.phone.value" />
                </div>
                <div class="field col-span-12">
                    <label>
                        About
                    </label>
                    <textarea v-model="userProfileForm.bio.value" placeholder="Write a short decription about yourself"
                        rows="4"
                        class="input-textarea w-full border border-[#CFD7FF] rounded-md px-4 py-2 focus:outline-none focus:ring-2 focus:ring-[#CFD7FF]"
                        required />
                </div>
                <div class="col-span-12 flex justify-end mt-6 mb-10">
                    <button
                        class="bg-[#2336DC] ml-auto  w-[250px]  h-[55px] gap-[4px] rounded-[8px] px-[50px] py-[6px] text-white">
                        Save Changes
                    </button>
                </div>
            </section>
            <section>
                <h1 class="text-lg font-semibold text-gray-800 text-[#101928]">Close Account</h1>
                <div class="field col-span-12 mt-6">
                    <label class="label">
                        We hate to see you go,tell us why and how to Improve
                    </label>
                    <input id="first_name" v-model="userProfileForm.name.value" type="text" placeholder="Tell us why"
                        class="w-full border border-[#CFD7FF] rounded-md px-4 py-2 focus:outline-none focus:ring-2 focus:ring-[#CFD7FF]  border-[1px] "
                        required>
                </div>

                <div class="col-span-12 flex justify-end mt-10 mb-10">
                    <button
                        class="bg-[#DC2323] ml-auto  w-[250px]  h-[55px] gap-[4px] rounded-[8px] px-[50px] py-[6px] text-white">
                        Close Account
                    </button>
                </div>
            </section>
        </main>
    </div>
</template>

<script setup lang="ts">

import { usePageHeader } from '@/composables/utils/header'
import { useUser } from '@/composables/auth/user'
import { useUpdateUserProfile } from '@/composables/auth/profile/edit'


const { user, id: user_id, userProfile } = useUser()
const { isDisabled, loading: profileLoading, populateData, update, updatePhoto, userProfileForm } = useUpdateUserProfile()


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

<style scoped></style>
