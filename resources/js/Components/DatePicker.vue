<script setup>
    const model = defineModel()

    const handleClick = (e) => {
        console.log(e);
    };
</script>

<template>
    <VDatePicker v-model="model" mode="date" @dayclick="handleClick"/>
</template>