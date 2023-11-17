<script setup>

    defineProps({
        buttonClass: {type: String, default: null},
        buttonData: {type: String, default: null},
    })


    defineEmits

</script>

<template>
    <button
        @click="summ"
        v-bind="{'data-operation':buttonData, 'class': buttonClass  }">
        <slot />
    </button>
</template>