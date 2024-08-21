<script setup>
    const props = defineProps({
        value: String
    });
</script>

<template>
    <select :value="value" @change="$emit('change', $event)" class="form-control">
        <option value="+">Adição</option>
        <option value="-">Subtração</option>
        <option value="*">Multiplicação</option>
        <option value="/">Divisão</option>
    </select>
</template>

