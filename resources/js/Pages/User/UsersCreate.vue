<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import {Head, useForm} from '@inertiajs/inertia-vue3';
import TextInput from "@/Components/TextInput.vue";
import InputLabel from "@/Components/InputLabel.vue";
import PrimaryButton from "@/Components/PrimaryButton.vue";

defineProps(["headers", "users"]);
const user = useForm({
    email: "",
    name: "",
    password: "",
    password_confirmation: "",
});


const createUser = () => {
    user.post(route("user.store"), {
        onSuccess: () => user.reset(),
    });
}


</script>

<template>
    <Head title="User"/>

    <AuthenticatedLayout>
        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="bg-white overflow-hidden shadow-sm sm:rounded-lg">
                    <div class="p-2">
                        <div class="md:grid md:grid-cols-3 md:gap-6">
                            <div class="mt-5 md:col-span-2 md:mt-0">
                                <form @submit.prevent="createUser">
                                    <div class="bg-white px-4 py-5 sm:p-6">
                                        <div class="grid grid-cols-6 gap-6">
                                            <div class="col-span-6 sm:col-span-3">
                                                <InputLabel
                                                    for="name"
                                                    value="Name"
                                                />
                                                <TextInput
                                                    id="name"
                                                    type="text"
                                                    class="mt-1 block w-full"
                                                    v-model="user.name"
                                                    required
                                                    autofocus
                                                />
                                            </div>
                                        </div>
                                        <div class="grid grid-cols-6 gap-6">
                                            <div class="col-span-6 sm:col-span-3">
                                                <InputLabel
                                                    for="email"
                                                    value="Email"
                                                />
                                                <TextInput
                                                    id="email"
                                                    type="email"
                                                    class="mt-1 block w-full"
                                                    v-model="user.email"
                                                    required
                                                    autofocus
                                                />
                                            </div>
                                        </div>
                                        <div class="grid grid-cols-6 gap-6">
                                            <div class="col-span-6 sm:col-span-3">
                                                <InputLabel
                                                    for="password"
                                                    value="Password"
                                                />
                                                <TextInput
                                                    id="password"
                                                    type="password"
                                                    class="mt-1 block w-full"
                                                    v-model="user.password"
                                                    required
                                                    autofocus
                                                />
                                            </div>
                                        </div>
                                        <div class="grid grid-cols-6 gap-6">
                                            <div class="col-span-6 sm:col-span-3">
                                                <InputLabel
                                                    for="confirm_password"
                                                    value="Confirm Password"
                                                />
                                                <TextInput
                                                    id="password_confirmation"
                                                    type="password"
                                                    class="mt-1 block w-full"
                                                    v-model="user.password_confirmation"
                                                    required
                                                    autofocus
                                                />
                                            </div>
                                        </div>
                                    </div>
                                    <div class="px-4 py-3 text-right sm:px-6">
                                        <PrimaryButton :disabled="useForm.processing">Save</PrimaryButton>
                                    </div>
                                </form>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </AuthenticatedLayout>
</template>
