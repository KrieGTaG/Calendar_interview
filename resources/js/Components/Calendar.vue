<script setup>
    import { computed, ref } from 'vue'
    import CalendarModal from '@/Components/CalendarModal.vue'

    const props = defineProps({
        date: {
            type: Date,
            default: new Date()
        },
        view: {
            type: Number,
            default: 4
        }
    });

    const isModalOpen = ref(false);

    const getDayCount = computed(() => {
        if(props.view === 0) return 1;
        if(props.view === 1) return 3;
        if(props.view === 2) return 5
        if(props.view === 3 || props.view === 4) return 7;
    });

    const getColClass = () => {
        console.log(getDayCount);
        // TODO
        return 'columns-7';
    };

    const daysOfTheWeek = ['Lundi', 'Mardi', 'Mercredi', 'Jeudi', 'Vendredi', 'Samedi', 'Dimanche'];

    const getStartOfWeek = (date) => {
        const start = new Date(date);
        const day = start.getDay();
        const difference = start.getDate() - day + (day === 0 ? -6 : 1); // adjust for week starting on Monday
        start.setDate(difference);
        start.setHours(0, 0, 0, 0); // set to start of the day
        return start;
    }

    // Function to get the current week dates
    const getCurrentWeekDates = computed(() => {
        const startOfWeek = getStartOfWeek(props.date);
        let week = [];
        for (let i = 0; i < 7; i++) {
            let day = new Date(startOfWeek);
            day.setDate(day.getDate() + i);
            week.push(day);
        }
        return week;
    });

    const showModal = () => {
        isModalOpen.value = true;
    };

</script>

<template>
    <div class="flex flex-row w-full">
        <div class="pt-24"><p v-for="timeSlot in 23" :key="timeSlot" class="h-20">{{timeSlot}}</p></div>
        <div :class="getColClass()" class="w-full">            
            <div v-for="(date, index) in getCurrentWeekDates" :key="index" class="border">
                <p>{{ date.getDate() }} {{ daysOfTheWeek[index] }}</p>
                <div v-for="timeSlot in 48" :key="timeSlot" class="border h-10" @click="showModal"></div>
            </div>
        </div>
    </div>
    <CalendarModal :show="isModalOpen" @close="isModalOpen=false"/>
</template>