<template>
    <div class="container">
        <div class="row justify-content-center">
            <div class="col-12 col-md-10 col-xl-8">
                <h2 class="mb-4">Todo App</h2>
                <AddTodo
                    @add-todo="addTodo"
                />
                <div class="filter pt-3 mb-4">
                    <h5>Фильтровать</h5>

                    <v-select
                        v-model="filter"
                        :options="['all', 'completed', 'not-completed']"
                        :clearable="false"
                        :searchable="false"
                    />
                </div>

                <hr>
                <TodoList
                    v-if="filteredTodos.length"
                    :todos="filteredTodos"
                    @remove-todo="removeTodo"
                />
                <p v-else>Нет ни одной заметки</p>
            </div>
        </div>
    </div>
</template>



<script>
    import TodoList from '@/components/TodoList';
    import AddTodo from  '@/components/AddTodo'

    export default {
        name: 'App',
        data() {
            return {
                todos: [
                    {id: 1, title: 'Сходить в магазин', completed: false},
                    {id: 2, title: 'Купить Пельмени', completed: false},
                    {id: 3, title: 'Купить Сок', completed: false},
                    {id: 4, title: 'Убить Билла', completed: false},
                ],
                filter: 'all',
            }
        },
        computed: {
            filteredTodos(){
                if (this.filter === 'all'){
                    return this.todos
                }

                if (this.filter === 'completed') {
                    return this.todos.filter(t => t.completed)
                }

                if (this.filter === 'not-completed') {
                    return this.todos.filter(t => !t.completed)
                }
            }
        },
        methods: {
            removeTodo(id) {
                this.todos = this.todos.filter(t => t.id !== id)
            },
            addTodo(todo){
                this.todos.push(todo)
            }
        },
        components: {
            TodoList, AddTodo
        }
    }
</script>

<style>
    .vs__selected-options {
        padding: 6px !important;
    }
</style>
