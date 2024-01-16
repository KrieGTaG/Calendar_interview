<script setup>
    import Modal from '@/Components/Modal.vue'

    const props = defineProps({
        show:  {
            type: Boolean, 
            default: true
        }
    })

    const emit = defineEmits(['close'])

    const closeModal = () => {
        emit('close');
    };

    const saveEvent = () => {
        
    };
</script>

<template>
    <Modal :show="show" :closeable="true">
        <div class="bg-white p-6 rounded-lg shadow-lg z-10 w-full">
            <div class="flex justify-between items-center mb-4">
                <h2>Date</h2>
                <button @click="closeModal">
                    <font-awesome-icon :icon="['fas', 'x']" />
                </button>
            </div>

            <div class="flex flex-row ">
                <div class="w-1/12 items-center flex">
                    <label for="evtName">
                        <font-awesome-icon :icon="['fas', 'calendar-days']"/>
                    </label>
                </div>
                <input type="text" name="evtName" placeholder="Event name" class="w-full rounded-md">
            </div>

            <div class="flex flex-row mt-3">
                <div class="w-1/12 items-center flex">
                    <label for="evtDesc" >
                        <font-awesome-icon :icon="['fas', 'comments']"/>
                    </label>
                </div>

                <textarea name="evtDesc" placeholder="Event description" class="w-full rounded-md"/>
            </div>


            <div class="mt-4 flex justify-end">
                <button
                @click="closeModal"
                class="px-4 py-2 mr-3 bg-gray-500 text-white rounded hover:bg-gray-700 transition duration-150"
                >
                    Close
                </button>
                <button
                @click="saveEvent"
                class="px-4 py-2  bg-blue-500 text-white rounded hover:bg-blue-700 transition duration-150"
                >
                    Save
                </button>
            </div>
        </div>
    </Modal>
</template>