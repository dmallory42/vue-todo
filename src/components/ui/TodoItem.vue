<template>
    <li class="flex" color="category.color">
        <label>
            <todo-checkbox v-on:change="onChange" :checked="done"></todo-checkbox>
            <span>&nbsp;</span>
        </label>
        <del v-if="done">{{ text }}</del>
        <span v-else>{{ text }}</span>
        <div class="space"></div>
        <button class="nes-btn is-error padding" v-on:click="$emit('removeTodo', id)">X</button>
    </li>
</template>

<script>
    import TodoCheckbox from "@/components/ui/TodoCheckbox";

    export default {
        name: "TodoItem",
        components: {TodoCheckbox},
        props: ['text', 'done', 'id'],
        methods: {
            onChange: function(done) {
                this.$emit('update:done', done)
            }
        }
    }
</script>

<style scoped>

</style>