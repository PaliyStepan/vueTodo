<template>
    <transition-group
        class="list-group"
        tag="ul"
    >
        <TodoItem
            v-for="(todo, i) in todos"
            v-bind:todo="todo"
            v-bind:index="i"
            v-on:remove-todo="removeTodo"
            :key="todo.id"
        />
    </transition-group>
</template>


<script>

import TodoItem from "./TodoItem"

export default {
    props: ['todos'],
    components: {
        TodoItem
    },
    methods:{
        removeTodo(id){
            this.$emit('remove-todo', id)
        }
    }
}
</script>


<style scoped>
    ul {
        list-style: none;
        padding: 0;
        margin: 0;
        width: 100%;
    }

    .anim-enter-active, .anim-leave-active {
        transition: all 0.1s ease-in-out;
    }

    .anim-enter, .anim-leave-to {
       /*transform: translateX(-100px);*/
        opacity: 0;
    }
</style>
