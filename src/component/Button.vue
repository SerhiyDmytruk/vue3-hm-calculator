<script setup>

    defineProps({
        buttonClass: {type: String, default: `rounded-lg h-20 w-20 flex items-center bg-indigo-800 justify-center shadow-lg border-2 border-indigo-700 hover:border-2 hover:border-gray-500 focus:outline-none`},
        buttonData: {type: String, default: null},
    })

    defineEmits(["summ", "clickTobtn", "clear"]);

</script>

<template>
    <button
        @click="$emit('summ')"
        v-bind="{'data-operation':buttonData, 'class': buttonClass  }">
        <slot />
    </button>
</template>