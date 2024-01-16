<script setup>
import ApplicationLogo from '@/Components/ApplicationLogo.vue';
import { Link } from '@inertiajs/vue3';
</script>

<template>
    <div class="min-h-screen flex flex-col sm:justify-center items-center pt-6 sm:pt-0 bg-gray-100 dark:bg-gray-900">
        <div class="flex flex-col justify-center content-center">
            <Link href="/" class="flex justify-center content-center">
                <font-awesome-icon :icon="['fas', 'calendar-days']" class="fa-5x" style="color: darkgray;"/>             
            </Link>
            <h1 class="mt-3 text-lg font-semibold"style="color: darkgray;" >Calendar App</h1>
        </div>

        <div
            class="w-full sm:max-w-md mt-6 px-6 py-4 bg-white dark:bg-gray-800 shadow-md overflow-hidden sm:rounded-lg flex flex-col"
        >
            <slot />
        </div>
    </div>
</template>
