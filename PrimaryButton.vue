<script setup>
    defineProps({
        type: {
            type: String,
            default: 'submit',
        },
        btnClass: {
            type: String,
        },
    });
</script>

<template>
    <button :type="type" :class="btnClass ? btnClass:'whitespace-nowrap gap-3 flex items-center text-white font-bold py-2.5 px-4 border border-black-800 bg-black-800 rounded-2 text-lg'">
        <slot />
    </button>
</template>
