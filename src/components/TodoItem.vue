<template>
    <div class="flex items-center place-content-between bg-white px-3 py-2">
        <form action="">
            <input type="checkbox" name="" id="">
        </form>
        <div class="text-blue-500">
            <span>{{todoitem.title}}</span>
        </div>
        <div class="flex items-center place-content-between  text-gray-500">
            <span>Fait le :</span>
            <span>25/01/2022 11:22</span>
        </div>
    </div>
</template>

<script>

    export default ({
    name : "TodoItem",
    props:{
        todoitem: Object
    }
    })
</script>
 