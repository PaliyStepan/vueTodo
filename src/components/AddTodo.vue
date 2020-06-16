<template>
    <form @submit.prevent="onSubmit" class="mb-3">
        <div class="input-group">
            <input type="text"  class="form-control" placeholder="Введите текст"
                   v-model="title">
            <button class="btn btn-primary ml-4">Create</button>
        </div>
    </form>
</template>

<script>
    export default {
        data(){
            return {
                title: ''
            }
        },
        methods: {
            onSubmit(){
                if (this.title.trim()){
                    const newTodo  = {
                        id: Date.now(),
                        title: this.title,
                        completed: false
                    };

                    this.$emit('add-todo', newTodo);
                    this.title = '';
                }
            }
        }
    }
</script>

<style scoped>
    .input-group {
        display: flex;
        align-items: center;
    }
    .input-group input {
        flex-grow: 1;
        border-radius: 5px !important;
    }
</style>
