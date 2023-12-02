<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { Head, useForm } from "@inertiajs/vue3";

const props = defineProps({
    title: String,
    user: Object,
});

const form = useForm({
    email: props.user.email,
    name: props.user.name,
    age: props.user.age,
    gender: props.user.gender
})
</script>

<template>
    <Head :title="props.title" />
    <AuthenticatedLayout>
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">Update User Profile</h2>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8 space-y-6">
                <div class="p-4 sm:p-8 bg-white shadow sm:rounded-lg">
                    <h2 class="text-lg font-medium text-gray-900">User Information</h2>

                    <form @submit.prevent="form.put(`/user/${user.id}`)">
                        <div class="form-control w-full">
                            <div class="label">
                                <span class="label-text">Email</span>
                            </div>
                            <input type="email" name="email" v-model="form.email" placeholder="Type here"
                                class="border-gray-300 focus:border-indigo-500 focus:ring-indigo-500 rounded-md shadow-sm" />
                        </div>
                        <div class="form-control w-full">
                            <div class="label">
                                <span class="label-text">Name</span>
                            </div>
                            <input type="text" name="name" v-model="form.name" placeholder="Type here"
                                class="border-gray-300 focus:border-indigo-500 focus:ring-indigo-500 rounded-md shadow-sm" />
                        </div>
                        <div class="form-control w-full">
                            <div class="label">
                                <span class="label-text">Age</span>
                            </div>
                            <input type="text" name="age" v-model="form.age" placeholder="Type here"
                                class="border-gray-300 focus:border-indigo-500 focus:ring-indigo-500 rounded-md shadow-sm" />
                        </div>
                        <div class="form-control w-full">
                            <div class="label">
                                <span class="label-text">Gender</span>
                            </div>
                            <input type="text" name="gender" v-model="form.gender" placeholder="Type here"
                                class="border-gray-300 focus:border-indigo-500 focus:ring-indigo-500 rounded-md shadow-sm" />
                        </div>

                        <input type="submit" :disabled="form.processing" value="Save"
                            class="inline-flex items-center mt-2 px-6 py-2 bg-gray-800 border border-transparent rounded-md font-semibold text-xs text-white uppercase tracking-widest hover:bg-gray-700 focus:bg-gray-700 active:bg-gray-900 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:ring-offset-2 transition ease-in-out duration-150">
                    </form>
                </div>
            </div>
        </div>
    </AuthenticatedLayout>
</template>