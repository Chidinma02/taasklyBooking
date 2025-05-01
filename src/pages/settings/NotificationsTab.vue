<template>
    <div>
        <div>
            <main class="flex flex-col gap-4 px-5 mt-4">

                <section class="border-b border-b-[#E9E9E9]">
                    <p class="page-title">Notifications</p>

                    <p class="text-[#0009448A] font-medium mb-6">Customize how you receive notifications from bookings
                        .
                    </p>
                </section>
                <section class="grid grid-cols-12 border-b border-b-[#E9E9E9] ">
                    <div class="col-span-10">
                        <p class="font-bold">General Notification</p>
                        <p class=" font-medium mt-5">Meeting Reminders.</p>
                        <p class=" text-[#0009448A] font-medium mt-1 mb-6">Get reminders a couple of days or hours
                            before
                            meetings
                        </p>
                    </div>
                    <div class="col-span-2 mt-2">
                        <div class="flex items-center justify-end mt-2">
                            <label class="relative inline-flex items-center cursor-pointer">
                                <input type="checkbox" class="sr-only peer" />
                                <div
                                    class="w-11 h-6 bg-gray-200 peer-focus:outline-none peer-focus:ring-2 peer-focus:ring-blue-500 rounded-full peer peer-checked:bg-[#2336DC] peer-checked:after:translate-x-full after:content-[''] after:absolute after:top-0.5 after:left-[2px] after:bg-white after:border-gray-300 after:border after:rounded-full after:h-5 after:w-5 after:transition-all">
                                </div>

                            </label>
                        </div>

                    </div>
                </section>
                <section class="grid grid-cols-12 border-b border-b-[#E9E9E9]">
                    <div class="col-span-10">
                        <p class="font-bold">Email Notifications</p>
                        <p class=" font-medium mt-5">Receive Updates via Email.</p>
                        <p class=" text-[#0009448A] font-medium mt-1 mb-6">Stay updated on all your meetings </p>
                    </div>
                    <div class="col-span-2 mt-2">
                        <div class="flex items-center justify-end mt-2">
                            <label class="relative inline-flex items-center cursor-pointer">
                                <input type="checkbox" class="sr-only peer" />
                                <div
                                    class="w-11 h-6 bg-gray-200 peer-focus:outline-none peer-focus:ring-2 peer-focus:ring-blue-500 rounded-full peer peer-checked:bg-[#2336DC] peer-checked:after:translate-x-full after:content-[''] after:absolute after:top-0.5 after:left-[2px] after:bg-white after:border-gray-300 after:border after:rounded-full after:h-5 after:w-5 after:transition-all">
                                </div>
                            </label>
                        </div>
                    </div>
                </section>
                <section class="grid grid-cols-12 border-b border-b-[#E9E9E9]">
                    <div class="col-span-10">
                        <p class="font-bold">Push Notifications</p>
                        <p class=" font-semibold mt-5">Enable Push Notifications.</p>
                        <p class=" text-[#0009448A] font-medium  mt-1 mb-6">Allow Bookings to send updates directly to
                            your device.
                        </p>
                    </div>
                    <div class="col-span-2 mt-2">
                        <div class="flex items-center justify-end mt-2">
                            <label class="relative inline-flex items-center cursor-pointer">
                                <input type="checkbox" class="sr-only peer" />
                                <div
                                    class="w-11 h-6 bg-gray-200 peer-focus:outline-none peer-focus:ring-2 peer-focus:ring-blue-500 rounded-full peer peer-checked:bg-[#2336DC] peer-checked:after:translate-x-full after:content-[''] after:absolute after:top-0.5 after:left-[2px] after:bg-white after:border-gray-300 after:border after:rounded-full after:h-5 after:w-5 after:transition-all">
                                </div>

                            </label>
                        </div>
                    </div>
                </section>
            </main>
        </div>
    </div>
</template>

<script setup lang="ts">

</script>

<style scoped></style>
