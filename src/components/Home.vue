<template>
    <div class="w-full">
        <div>
            <NavBar />
        </div>
        <div>
            <Forms />
        </div>
        
        <div class="bg-blue-200 space-y-2 px-4 py-3 text-white mb-1">
            <div class="">
                //badges
            </div>
            <div>
                <todo-item v-for="todoitem in todoItems" :key="todoitem" :todoitem="todoitem" />
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
                todoItems:[
                    {
                        title: " sors les poubelles",
                        end_at: " sors les poubelles",
                        done: false,
                        done_at: null,
                    },
                       {
                        title: " fais la vaissaille",
                        end_at: " 12/02/22 11:21:22",
                        done: false,
                        done_at: null,
                    },
                       {
                        title: " fais la lessive",
                        end_at: " sors les poubelles",
                        done: false,
                        done_at: null,
                    },
                       {
                        title: " programme un peu",
                        end_at: " sors les poubelles",
                        done: false,
                        done_at: null,
                    }
                ]
            }
        }

    }
</script>
