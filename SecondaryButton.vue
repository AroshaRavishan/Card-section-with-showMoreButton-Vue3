<script setup>
    defineProps({
        btnClass: String,
        type: {
            type: String,
            default: 'button',
        },
    });
</script>

<template>
    <button :type="type" :class="btnClass ? btnClass: 'whitespace-nowrap gap-3 flex items-center text-black-800 font-bold py-2.5 px-4 border border-black-800 bg-transparent rounded-2 text-lg'">
        <slot />
    </button>
</template>
