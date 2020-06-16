<template>
    <li className="list-group-item">
        <label
            class="label"
            :class="{done: todo.completed}"
        >
            <input type="checkbox"
               v-on:change="todo.completed = !todo.completed"
               :checked="todo.completed"
            >
            <span class="custom-check">

            </span>
            {{todo.title | uppercase}}
        </label>
        <button v-on:click="$emit('remove-todo', todo.id)" class="btn btn-danger">&times;</button>
    </li>
</template>

<script>
export default {
    props: {
        todo:{
            type: Object,
            required: true
        },
        index: Number
    },
    filters: {
        uppercase(value){
            return value.toUpperCase()
        }
    }
}
</script>

<style scoped>
    li {
        border: 1px solid #ccc;
        padding: 10px 16px;
        margin-bottom: 15px;
        display: flex;
        align-items: center;
        justify-content: flex-start;
    }

    .done {
        text-decoration: line-through;
    }


    .btn {
        font-size: 25px;
        padding: 10px 6px;
        line-height: 0.3;
    }

    .label {
        position: relative;
        margin: 0;
        margin-right: 15px;
        cursor: pointer;
        display: inline-flex;
        align-items: center;
        text-align: left;
    }

    .label input {
        position: absolute;
        top: 50%;
        transform: translateY(-50%);
        left: 0;
        width: 1px;
        height: 1px;
        opacity: 0;
    }

    .label input:checked ~ .custom-check:before {
        opacity: 1;
    }

    .custom-check {
        width: 15px;
        min-width: 15px;
        height: 15px;
        display: inline-block;
        border: 1px solid #000;
        -webkit-border-radius: 2px;
        -moz-border-radius: 2px;
        border-radius: 2px;
        margin-right: 16px;
        position: relative;
    }

    .custom-check:before {
        position: absolute;
        width: 100%;
        height: 100%;
        top: 0;
        left: 0;
        content: '';
        background-image: url("../assets/check.svg");
        background-position: center;
        background-repeat: no-repeat;
        background-size: 12px;
        opacity: 0;
        transition: all 0.2s ease;
    }


    @media only screen and (max-width: 575px) {
        .label {
            min-width: auto;
            width: 100%;
        }
    }



</style>
