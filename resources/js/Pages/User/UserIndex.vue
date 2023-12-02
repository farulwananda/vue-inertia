<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { Head, Link } from '@inertiajs/vue3'

defineProps({
  title: String,
  users: Object
})
</script>

<template>
  <Head :title="title" />

  <AuthenticatedLayout>
    <template #header>
      <h2 class="font-semibold text-xl text-gray-800 leading-tight">User Account</h2>
    </template>

    <div class="py-12">
      <div class="max-w-7xl mx-auto sm:px-6 lg:px-8 md:w-auto">
        <Link :href="route('user.create')"
          class="inline-flex items-center mb-2 px-6 py-2 bg-gray-800 border border-transparent rounded-md font-semibold text-xs text-white uppercase tracking-widest hover:bg-gray-700 focus:bg-gray-700 active:bg-gray-900 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:ring-offset-2 transition ease-in-out duration-150">
        Add User</Link>
        <div class="bg-white overflow-hidden shadow-sm sm:rounded-lg">

          <table class="table">
            <!-- head -->
            <thead>
              <tr class="text-center">
                <th>No</th>
                <th>Name</th>
                <th>Email</th>
                <th>Age</th>
                <th>Gender</th>
                <th>Action</th>
              </tr>
            </thead>
            <tbody>
              <!-- row 1 -->
              <tr v-for="user in users">
                <th class="text-center">{{ user.id }}</th>
                <td>{{ user.name }}</td>
                <td>{{ user.email }}</td>
                <td>{{ user.age }}</td>
                <td>{{ user.gender }}</td>
                <td class="text-center">
                  <Link :href="route('user.edit', user.id)"
                    class="btn btn-sm btn-warning px-6 ml-2 py-2 rounded-sm max-w-xs">
                  Edit</Link>
                  <Link :href="route('user.destroy', user.id)" method="delete"
                    class="btn btn-sm btn-error px-4 ml-2 py-2 rounded-sm max-w-xs">
                  Delete
                  </Link>
                </td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </AuthenticatedLayout>
</template>
