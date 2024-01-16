<script setup>
    import { ref, onMounted, onUnmounted } from 'vue';

    const isOpen = ref(false);
    const dropdown = ref(null);

    const toggleDropdown = () => {
    isOpen.value = !isOpen.value;
    };

    const handleClickOutside = (event) => {
    if (dropdown.value && !dropdown.value.contains(event.target)) {
        isOpen.value = false;
    }
    };

    onMounted(() => {
    document.addEventListener('click', handleClickOutside);
    });

    onUnmounted(() => {
    document.removeEventListener('click', handleClickOutside);
    });
</script>

<template>
    <div class="flex flex-row">
        <div class="basis-3/12">
            <button>X</button>
            <button><</button>
            <button>></button>
        </div>
        <div class="basis-6/12">
                Emplacement
        </div>
        <div class="basis-3/12">
            <div class="relative" ref="dropdown">
                <button @click="toggleDropdown" class="px-4 py-2 text-white bg-blue-500 rounded hover:bg-blue-600">
                    Dropdown
                </button>
                <div v-if="isOpen" class="absolute right-0 w-48 py-2 mt-2 bg-white rounded shadow-xl">
                    <a href="#" class="block px-4 py-2 text-gray-800 hover:bg-gray-100">Link 1</a>
                    <a href="#" class="block px-4 py-2 text-gray-800 hover:bg-gray-100">Link 2</a>
                    <a href="#" class="block px-4 py-2 text-gray-800 hover:bg-gray-100">Link 3</a>
                </div>
            </div>
        </div>
    </div>
</template>