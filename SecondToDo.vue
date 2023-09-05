<template>
    <div class="ContainerToDo">
        <div class="outsideToDo">
            <div class="group-add">
                <input type="text" placeholder="ToDo">
                <button>Add</button>
            </div>
            <div class="group-work">
                <div class="group-checkbox">
                    <input type="checkbox" name="abc" id="number1">
                    <p>Tại đây</p>
                </div>
                <div class="group-button">
                    <button class="btn-update">Update</button>
                    <button class="btn-delete">Delete</button>
                </div>
            </div>
        </div>
    </div>
</template>
    
<script>
export default {
    name: 'SecondToDo',
    props:{},
    data() {
        return {
        }
    },

    methods: {

    }
}

</script>

<style scoped>

    .ContainerToDo{
        display: flex;
        justify-content: center;
    }

    .ContainerToDo .outsideToDo{
        display: flex;
        flex-direction: column;
        margin-top: 30px;
        width: 600px;
        justify-content: space-between;
        align-self: center;
        border: 2px solid black;
        padding: 20px;
    }
    .group-add{
        display: flex;
        justify-content: space-evenly;
        margin: 10px;
    }

    .group-add input{
        width: 400px;
        padding: 15px;
        border-radius: 10px;
    }

    .group-add button {
        border-radius: 5px;
        padding: 0 20px;
        color: green;
        background-color: aqua;
    }

    .group-work{
        display: flex;
        justify-content: space-between;
    }

    .group-checkbox{
        display: flex;
    }

    .group-button{
        display: flex;
        gap: 20px;
    }

    .group-work .group-button button{
        color: red;
    }
</style>