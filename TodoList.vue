<template>
    <div class='todo-list-container'>
        <div class="container">
            <div class="group-input">
                <input v-model="todo" type="text" placeholder="TodoList">
                <button @click="addTodo" class="addTodo">Add</button>
            </div>
            <small style="color: red;">{{ error }}</small>
            <div class="group-checkbox" v-for="(item, index) in todoList" :key="index">
                <div class="index">
                    <input type="checkbox" name="abc" id="number1">
                    <p v-if="!item.isUpdate">{{ item.title }}</p>
                    <input v-model="addComfirm" type="text" v-else>
                </div>

                <div class="button-btn">
                    <button @click="HandleUpdate(item.id)" v-if="!item.isUpdate" class="update-btn">Update</button>
                    <button @click="HandleDelete(item.id)" v-if="!item.isUpdate" class="delete-btn">Delete</button>
                    <button @click="HandleConfirm(item.id)" v-else>Confirm</button>
                </div>

            </div>
        </div>

    </div>
</template>
  
<script>
//name trong commodent luôn luôn có 2 âm tiết
export default {
    name: 'TodoListVue',
    props: {},
    data() {
        return {
            todo: "",
            todoList: [],
            error:'',
            addComfirm:'',
        }
    },
    methods: {
        addTodo() {
            this.error='';
            if(this.todo.length===0){
                this.error = 'Error Message'
            } else if(this.todo.length<=5){
                this.error = 'Error 1'
            } else {
                const form = {
                id: this.todoList.length,
                title: this.todo,
                isUpdate: false,
            }
            // console.log(form);
            this.todoList.push(form);
            this.todo = ''
            // console.log(this.todoList);
            }
        },
        HandleUpdate(id){
            this.todoList[id].isUpdate = true;
            this.addComfirm = this.todoList[id].title;
        },
        HandleConfirm(){
            
        }
    }
}
</script>
    
  <!-- scoped là chỉ dùng style(css) trong file này-->
<style scoped>
.todo-list-container {
    display: flex;
    justify-content: center;
}

.todo-list-container .container {
    margin-top: 20px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    width: 500px;
    align-self: center;
}

.group-input {
    display: flex;
    align-self: center;
}

.group-input input {
    width: 300px;
    border-radius: 5px;
    border: 1px solid black;
    padding: 10px;
}

.group-input button {
    color: red;
    background-color: green;
    border-radius: 5px;
    padding: 0 10px;
}

.group-checkbox {
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.group-checkbox .index {
    display: flex;
}

.group-checkbox .button-btn {
    display: flex;
    gap: 10px;
}

.group-checkbox .button-btn button {
    border-radius: 5px;
    background-color: gold;
    border: 1px solid black;
    padding: 5px;
}
</style> 