<template>
    <div class="flex items-center place-content-between bg-white px-3 py-2">
        <div class="flex space-x-2">
            <form v-if="!todoitem.done" action="">
                <input type="checkbox" name="" v-model="todoitem.done" @change="setCompleted_at(todoItemKey, new Date().toUTCString())">
            </form>
            <div class="text-blue-500 " >
                <span v-if="!todoitem.done">{{todoitem.title}} </span>
                <span v-if="todoitem.done" class="line-through">{{todoitem.title}}</span>
            </div>

        </div>
        <div class="flex items-center place-content-between  text-gray-500 space-x-6">
            <span v-if="!todoitem.done" class=" hidden sm:block ">
                <span>Avant le : </span>
                <span>{{todoitem.end_at}}</span>
            </span>
            <span v-if="todoitem.done" class="text-green-400  hidden sm:block ">
                <span>Fait le : </span>
                <span>{{todoitem.done_at}}</span>
            </span>
            <span class="text-red-500" @click="deleteItem(todoItemKey)"> 
                <i class="fas fa-trash-alt"></i>
            </span>
        </div>
    </div>
</template>

<script>

    export default ({
        name : "TodoItem",
        props:['todoitem',"setCompleted_at", "todoItemKey", "deleteItem"],
        methods:{}
    })
</script>
 