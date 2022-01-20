<template>
    <div class="bg-blue-500 flex place-content-between items-center px-3 py-2 text-white">
        <div class="">
            <span class="text-2xl"> TodoList </span>
        </div>
        <div>
            <button v-if="!action" @click="toggleForm" class="p-2 px-3 rounded-xl text-white bg-green-500"> <i  class='fas fa-plus'></i> &nbsp; Ajouter</button>
            <button v-if="action" @click="toggleForm" class="p-2 px-3 rounded-xl text-white bg-red-500"> <i  class='fas fa-times'></i> &nbsp; Fermer</button>
        </div>
    </div>
</template>

<script>
 // import { defineComponent } from '@vue/composition-api'

export default ({
   name : "NavBar",
   props:["toggleForm", "action"]
   
})
</script>
 