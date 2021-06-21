<template>
    <div class="app-panel">
        <div class="form">
            <input type="text" class="task-input" v-model="newTask"/>
            <button class="task-button" @click="addTask">Add Task</button>
        </div>    
        <div class="task">
            <Header msg="To do Tasks"/>
            <div v-if="task.length==0">No task to complete</div>
            <div v-else>
                <li v-for="(t, index) in task" :key="t">
                    <h5>{{index}}. {{t}}</h5> 
                   
                    <button class="done-btn"  @click="completeTask(t)">Done</button>
                    <button class="delete-btn"  @click="deleteTask(t)">Delete</button>
                </li>
            </div>
        </div>
        <div class="done">
            <Header msg="Done Tasks"/>
            <div v-if="done.length==0">No task is complete</div>
            <div v-else>
                <li v-for="(t, index) in done" :key="t">
                    <h5>{{index}}. {{t}}</h5> 
                   
                    <button class="undo-btn"  @click="undoDone(t)">Undo</button>
                    <button class="delete-btn"  @click="deleteDone(t)">Delete</button>
                </li>
            </div>
        </div>    
    </div>

</template>


<style scoped>
.app-panel{
    width:100%;
    height: 100%;
}
.form{
    float: left;
    width: auto;
    margin: 20px;
}
.task{
    width: 300px;
    float: left;
}
.done{
    width: 300px;
    float: left;
}
.task-input{
    border: 1px solid gray;
    border-radius: 5px;
    height: 30px;
}
.task-button, .undo-btn{
    background-color: blue;
    color: #fff;
    border: 0px;
    padding: 10px 20px;
}
.task li, .done li{
    list-style-type: none;
    border: 1px solid #c2c2c2;
    width: 200px;
    height: 120px;
    border-radius: 5%;
    margin: 5px 0px;
    padding-top: 10px;
}
.done-btn{
    border:0px;
    color: white;
    background-color: crimson;
    float: right !important;
    border-radius: 5%;
    padding: 10px 20px;
    margin: 0px 10px;
}
.delete-btn{
    border:0px;
    color: white;
    background-color: red;
    float: right !important;
    border-radius: 5%;
    padding: 10px 20px;
    margin: 0px 10px;
}
</style>


<script>
//import func from '../../vue-temp/vue-editor-bridge';
import Header from './Header.vue';
export default {
    name: 'ToDo',
    components:{
        Header
    },
    data(){
        return{
            newTask: '',
            task: [],
            done: []
        };
    },
    methods:{
        addTask(){
            //console.log(this.newTask);
            this.task.push(this.newTask);
            //console.log(this.task);
        },
        completeTask(t){
            console.log(t);
            this.task= this.task.filter(function(ele){
                return ele!=t;

            });
            this.done.push(t);
            console.log(this.done);
        },
        deleteTask(t){
            //console.log(this.task);
            this.task= this.task.filter(function(ele){
                return ele!=t;

            })
            console.log(this.task);
        },
        deleteDone(t){
            //console.log(this.task);
            this.done= this.done.filter(function(ele){
                return ele!=t;

            })
            console.log(this.done);
        },
        undoDone(t){
            this.done= this.done.filter(function(ele){
                return ele!=t;

            });
            this.task.push(t);
        }

    }
}
</script>