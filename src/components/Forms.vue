<template>
    <div class="bg-blue-200 ">
        <div v-if="!action" class="flex place-content-between items-center px-4 py-3 text-white mb-1">
            <div class="text-gray-500">Tirer par: </div>
            <div class="">
                <select name="" id="display_mode_form" class=" bg-white text-gray-700 px-3 py-2 w-full" v-model="selectValue"  @change="updateDisplayItem()">
                    <option value="all" selected="selected" >Toutes</option>
                    <option value="notDone">En cours...</option>
                    <option value="done">Terminées</option>
                </select>
            </div>
        </div>
        <div v-else class="px-4 py-3 mb-1 space-y-2">
            <div>
                <ul>
                    <li v-for="error in message_error" :key="error" class="text-red-500">
                        {{error}}
                    </li>
                </ul>
            </div>
            <input type="text" placeholder="entrez le titre de votre tache ... "  v-model="todoitem.title" class="block bg-white text-gray-700 px-2 py-1 w-full">
            <input type="datetime-local" placeholder="La date de fin de votre tache..." v-model="todoitem.end_at" class="block bg-white text-gray-700 px-2 py-1 w-full" >
            <div class="flex justify-end">
                <button class="bg-green-500 px-3 py-1 text-center text-white rounded-md right-0" @click="verifyBeforSend()"><i  class='fas fa-plus'></i> &nbsp; Ajouter</button>
            </div>

        </div>
    </div>
</template>

<script>

    export default ({
        name : "Froms",
        props:['action', "addItem", "toggleForm","displayItems","setDisplayItems"],
        data:function () {
            return {
                todoitem: {
                    title: null,
                    end_at: null,
                    done: false,
                    done_at: null,
                },
                message_error:[],
                selectValue : this.displayItems
            }
        
        },
        methods:{
            verifyBeforSend(){
                let testPassed = 0
                if(this.todoitem.title != null){
                    testPassed +=1
                    if(this.todoitem.title.length > 5){
                        testPassed +=1
                    }else{
                        this.message_error.push("Le titre doit avoir plus de 5 caracteres" )
                    }
                }else{
                    this.message_error.push("Nous n'avez pas saisit de titre" )
                }


                if(this.todoitem.end_at != null){
                    testPassed +=1
                    if(new Date(this.todoitem.end_at).getTime() >= new Date() ){
                        testPassed +=1
                    }else{
                        this.message_error.push("la date de fin ne peut pas etre inférieure à maintenant" )
                    }
                }else{
                    this.message_error.push("Nous n'avez pas indiqué de date" )
                }
                if(testPassed == 4){
                    this.addItem(this.todoitem)
                    this.toggleForm()
                }
            },
            updateDisplayItem(){
                this.setDisplayItems(this.selectValue)
            }
        },
        computed:{
            cleanErrors(){
                return 1 
            }
        }


    })
</script>
 