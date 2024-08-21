<script setup>
    const props = defineProps({
        value: Number,
        placeholder: String
    });
</script>

<template>
    <input 
        type="number" 
        :value="value" 
        @input="$emit('input', $event)" 
        class="form-control"
        :placeholder="placeholder"
    />
</template>


