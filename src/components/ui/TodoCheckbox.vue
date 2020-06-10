<template>
    <input
        type="checkbox"
        class="nes-checkbox"
        v-bind:checked="checked"
        v-on:change="$emit('change', $event.target.checked)"
    >
</template>

<script>
    export default {
        name: "TodoCheckbox",
        model: {
            prop: 'checked',
            event: 'change'
        },
        props: ['checked']
    }
</script>

<style scoped>

</style>