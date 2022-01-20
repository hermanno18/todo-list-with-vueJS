<template>
    <div class="w-full">
        <div>
            <NavBar :toggleForm="toggleForm" :action="formAction"  />
        </div>
        <div>
            <Forms :toggleForm="toggleForm" :action="formAction" :addItem="addItem" :displayItems="displayItems" :setDisplayItems="setDisplayItems"/>
        </div>
        
        <div class="bg-blue-200 space-y-2 px-4 py-3 text-white mb-1">
            <div class="space-x-4">
                <span class="bg-green-500 px-2 py-1 text-white rounded-sm">Aujourd'hui</span> 
                <i class="fas fa-angle-double-right text-gray-500"></i>
                <span v-if="displayItems ==='all'" class="bg-green-500 px-2 py-1 text-white rounded-sm ">Toutes les taches</span>
                <span v-else-if="displayItems ==='notDone'" class="bg-green-500 px-2 py-1 text-white rounded-sm">taches en cours</span>
                <span v-else-if="displayItems ==='done'" class="bg-green-500 px-2 py-1 text-white rounded-sm">taches terminées</span>
            </div>
            <div v-if="displayItems === 'all'">
                <todo-item v-for="(todoitem, i)  in todoItems" :key="i" :todoItemKey="i"  :todoitem="todoitem" :setCompleted_at="set_completed_at" :deleteItem="deleteItem" />
            </div>

            <div v-else-if="displayItems === 'notDone'">
                <div v-for="(todoitem, i)  in todoItems" :key="i">
                    <todo-item v-if="!todoitem.done"  :todoItemKey="i"  :todoitem="todoitem" :setCompleted_at="set_completed_at" :deleteItem="deleteItem" />
                </div>
            </div>

            <div v-else-if="displayItems === 'done'">
                <div v-for="(todoitem, i)  in todoItems" :key="i">
                    <todo-item v-if="todoitem.done"  :todoItemKey="i"  :todoitem="todoitem" :setCompleted_at="set_completed_at" :deleteItem="deleteItem" />
                </div>
            </div>
            <div v-if="todoItems.length == 0" class="text-center">
                <p class="text-gray-600">Il n'y a pas encore de taches pour l'instant</p>
            </div>
        </div>
    </div>
</template>

<script>
import NavBar from "./NavBar.vue"
import Forms from "./Forms.vue"
import TodoItem from "./TodoItem.vue"

    export default {
        name: "home",
        components:{
            NavBar,
            Forms,
            TodoItem,
        },
        data : function(){
            return {
                todoItems:[],
                formAction: false,
                displayItems:"all",
            }
        },
        methods:{
            set_completed_at(key, value){

                this.todoItems[key].done_at=value
            },
            deleteItem(key){
                delete this.todoItems[key] 
            },
            toggleForm(){
                this.formAction = !this.formAction
            },
            addItem(item){
                this.todoItems.unshift(item)
            },
            setDisplayItems(value){
                this.displayItems=value
            }
        },

    }
</script>
