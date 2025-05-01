<template>
    <div>
        <div>
            <main class="flex flex-col gap-4 px-5 mt-4">
                <section class="border-b border-b-[#E9E9E9]">
                    <p class="page-title">Security</p>
                    <p class="text-[#0009448A] font-medium mb-6">Manage your passwords and we’ll make sure your
                        account is
                        safe.</p>
                </section>
                <section>
                    <span class="flex items-center justify-between my-4 mt-6">
                        <div>
                            <h1 class="text-lg font-semibold text-gray-800 text-[#101928]">
                                Passwords
                            </h1>
                            <p class="text-[#0009448A] font-medium">Manage your passwords.</p>
                        </div>
                    </span>
                </section>
                <!-- <section id="uneditable" class="grid sm:grid-cols-2 md:grid-cols-3 mt-8 gap-x-4 gap-y-8"> -->
                <section id="uneditable" class="grid grid-cols-12  mt-6 gap-x-4 gap-y-8  border-b border-b-[#E9E9E9]">
                    <div class="field col-span-6">
                        <label>
                            Old password
                        </label>
                        <input id="first_name" type="text" placeholder="Okubote Eniola"
                            class="w-full border border-[#CFD7FF] rounded-md px-4 py-2 focus:outline-none focus:ring-2 focus:ring-[#CFD7FF]  border-[1px] "
                            required>
                    </div>
                    <div class="field col-span-6">
                        <label>
                            New password
                        </label>
                        <input id="email" type="text"
                            class="w-full border border-[#CFD7FF] rounded-md px-4 py-2 focus:outline-none focus:ring-2 focus:ring-[#CFD7FF]"
                            placeholder="Enter Email" required>
                    </div>
                    <div class="col-span-12">
                        <p class="text-[#0009448A] font-medium">Your password should be 8 letters long with an upper
                            case
                            and a special character.</p>
                    </div>
                    <div class="col-span-12 flex justify-end mt-6 mb-10">
                        <button
                            class="bg-[#2336DC] ml-auto  w-[250px]  h-[55px] gap-[4px] rounded-[8px] px-[50px] py-[6px] text-white">
                            Save Changes
                        </button>
                    </div>
                </section>
                <section class="grid grid-cols-12">
                    <div class="col-span-10">
                        <p class=" font-semibold">2-Step Verification.</p>
                        <p class=" text-[#0009448A] font-medium">Add an extra layer of protection during login</p>
                    </div>
                    <div class="col-span-2">
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
