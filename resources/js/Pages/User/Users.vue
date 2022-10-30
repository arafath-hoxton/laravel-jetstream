<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import {Head} from '@inertiajs/inertia-vue3';
import VueTable from '@/Components/VueTable.vue';
import SectionTitle from '@/Components/SectionTitle.vue';
import PrimaryButton from '@/Components/PrimaryButton.vue';
import NavLink from '@/Components/NavLink.vue';

defineProps(["headers", "users"]);
</script>

<template>
    <Head title="User"/>

    <AuthenticatedLayout>
        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="bg-white overflow-hidden shadow-sm sm:rounded-lg">
                    <div class="p-2">
                        <SectionTitle>
                            <template #title>
                                Users
                            </template>
                            <template #description>
                                All users
                            </template>
                            <template #aside>
                                <NavLink :href="route('user.create')">
                                    <PrimaryButton>Add User</PrimaryButton>
                                </NavLink>
                            </template>
                        </SectionTitle>
                    </div>
                    <VueTable :headers="headers" :items="users.data"></VueTable>
                </div>
            </div>
        </div>
    </AuthenticatedLayout>
</template>
