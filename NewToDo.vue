<template>
    <div class="container-todo">
        <div class="outside-todo">
            <div class="group-input">
                <input @keydown.enter="addToDo" v-model="todo" type="text" placeholder="ToDo-List">
                <button :disabled="isDisable" @click="addToDo" class="addToDo">Add</button>
            </div>
            <small>{{ errorMessage }}</small>
            <div class="group-title" v-for="(item, index) in todoList" :key="index">
                <div class="index-title">
                    <input v-model="item.isDone" :disabled="isDisable" type="checkbox" name="abc" id="number1">
                    <p v-if="!item.isUpdate" :style="{'text-decoration': item.isDone ? 'line-through' : 'none'}" >{{ item.title }}</p>
                    <input v-model="addComfirm" type="text" v-else>
                </div>
                <div class="group-button">
                    <button @click="handleUpdate(item.id)" v-if="!item.isUpdate" :disabled="isDisable"
                        class="btn-update">Update</button>
                    <button @click="handleDelete(item.id)" v-if="!item.isUpdate" :disabled="isDisable"
                        class="btn-delete">Delete</button>
                    <button @click="handleComfirm(item.id)" v-else class="btn-comfirm">Comfirm</button>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name: 'NewToDo',
    props: {},
    data() {
        return {
            todo: "",
            todoList: [],
            errorMessage: '',
            addComfirm: '',
            isDisable: false,
        }
    },
    methods: {
        // handleKeyDown(e){
        //     if(e.key === 'Enter'){
        //         this.addToDo()
        //     }
        // },

        addToDo() {
            this.errorMessage = '';
            if (this.todo.length === 0) {
                this.errorMessage = "Error Message"
            } else {
                const form = {
                    id: this.todoList.length,
                    title: this.todo,
                    isUpdate: false,
                    isDone: false,
                }
                this.todoList.push(form);
                console.log();
                this.todo = '';
            }
        },
        handleUpdate(id) {
            // console.log(this.todoList);
            this.todoList[id].isUpdate = true;
            this.addComfirm = this.todoList[id].title;
            this.isDisable = true;

        },
        handleComfirm(id) {
            this.todoList[id].isUpdate = false;
            this.todoList[id].title = this.addComfirm;
            this.isDisable = false;
        },
        handleDelete(id) {
            this.todoList = this.todoList.filter((item) => item.id !== id);
        }
    }
}
</script>
<style scoped>
.container-todo {
    display: flex;
    justify-content: center;
}

.container-todo .outside-todo {
    margin-top: 30px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    width: 600px;
    align-self: center;
    border: 3px solid orange;
    box-shadow: 0 20px 50px #000000ff;
    border-radius: 20px;
}

small {
    margin: 5px;
    color: red;
}

.group-input {
    display: flex;
    /* align-self: center; */
    justify-content: space-evenly;
    margin-top: 5px;
}

.group-input input {
    width: 300px;
    padding: 5px;
    border: 1px solid black;
    border-radius: 6px;
}

.group-input button {
    color: red;
    background-color: green;
    border-radius: 5px;
    padding: 0 10px;
}

.group-title {
    display: flex;
    justify-content: space-between;
    align-items: center;
    border: 5px solid gray;
    border-radius: 10px;
    margin: 10px;
}

.group-title .index-title {
    display: flex;
    gap: 10px;
}

.group-title .group-button {
    display: flex;
    gap: 10px;
    margin-right: 2px;
}

.group-title .group-button button {
    border-radius: 5px;
    padding: 5px;
    border: 1px solid black;
}

.group-title .group-button .btn-update {
    background-color: yellow;
}

.group-title .group-button .btn-delete {
    background-color: red;
    color: white;
}

.group-title .group-button .btn-delete[disabled] {
    background-color: gray;
}

.group-title .group-button .btn-update[disabled] {
    background-color: gray;
}
</style>
