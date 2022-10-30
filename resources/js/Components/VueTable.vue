<script setup>
import NavLink from "@/Components/NavLink.vue";

defineProps(["headers", "items"]);
</script>

<template>
    <div class="table w-full p-2">
        <table class="w-full border">
            <thead>
            <tr class="bg-gray-50 border-b">
                <th class="p-2 border-r cursor-pointer text-sm font-thin text-gray-500"
                    scope="col"
                    v-for="header in headers"
                    :key="header"
                >
                    <div class="flex items-center justify-center">
                        {{ header }}
                    </div>
                </th>
            </tr>
            </thead>
            <tbody>
            <tr class="bg-gray-100 text-center border-b text-sm text-gray-600" v-for="item in items" :key="item">
                <td class="p-2 border-r"
                    v-for="(td, tdIndex) in item"
                    :key="tdIndex"
                >
                    <NavLink :href="td"
                             v-if="tdIndex === 'action'"
                    >View
                    </NavLink>
                    <span v-else> {{ td }}</span>
                </td>
            </tr>
            </tbody>
        </table>
    </div>
</template>
