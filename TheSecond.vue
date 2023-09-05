<template>
    <div class='thesecond-container'>
        <div class="group-table">
            <table>
                <thead>
                    <tr>
                        <th>NO.</th>
                        <th>FullName</th>
                        <th>Class</th>
                        <th>Math</th>
                        <th>Physics</th>
                        <th>Chemistry</th>
                        <th>Average</th>
                        <th>Fix</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="(item, index) in classList" :key="index" >
                        <td>{{ index + 1 }}</td>
                        <td>{{ fullname(item.firstname, item.lastname) }}</td>
                        <td>{{ item.class }}</td>
                        <td>{{ item.math }}</td>
                        <td>{{ item.physics }}</td>
                        <td>{{ item.chemistry }}</td>
                        <td>{{ average(item.math, item.physics, item.chemistry) }}</td>
                        <td>
                            <button @click="handleUpdate(index)">Update</button>
                            <button>Delete</button>
                        </td>
                    </tr>
                </tbody>
            </table>
        </div>
        <div v-if="tableUpdate" class="group-update">
            <h2>Update</h2>
            <div class="content-input">
                <div class="group-input">
                    <p>Full name:</p>
                    <input type="text" v-model="fullNameUpdate">
                </div>
                <div class="group-input">
                    <p>Class:</p>
                    <input type="text" v-model="classUpdate">
                </div>
                <div class="group-input">
                    <p>Math:</p>
                    <input type="number" v-model="scoreMath">
                </div>
                <div class="group-input">
                    <p>Physics:</p>
                    <input type="number" v-model="scorePhysics">
                </div>
                <div class="group-input">
                    <p>Chemistry:</p>
                    <input type="number" v-model="scoreChemistry">
                </div>
            </div>
            <div class="group-button">
                <button >Confirm</button>
                <button>Cancel</button>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'TheSecond',
    props: {},
    components: {},
    data() {
        return {
            classList: [
                {
                    firstname: 'Nguyen',
                    lastname: 'B',
                    class: '1C',
                    math: 9,
                    physics: 10,
                    chemistry: 9.5
                },
                {
                    firstname: 'Le',
                    lastname: 'A',
                    class: '2C',
                    math: 9.2,
                    physics: 9.8,
                    chemistry: 9
                },
                {
                    firstname: 'Nguyen',
                    lastname: 'B',
                    class: '3C',
                    math: 9.2,
                    physics: 8.9,
                    chemistry: 10
                },
            ],
            getIndex: null,
            plusMark: null,
            tableUpdate: false,
            fullNameUpdate: '',
            classUpdate: '',
            scoreMath: '',
            scorePhysics: '',
            scoreChemistry: '',
        }
    },
    computed: {
        // fullNameUpdate() {
        //     const item = this.classList[this.index];
        //     return this.fullname(item.firstname, item.lastname);
        // }
    },
    watch: {
        plusMark() {
            this.classList = this.classList.map(item => {
                item.math = item.math + Number(this.plusMark);
                return item;
            });
        }
    },
    methods: {
        getIndex(index){
            this.getIndex = this.classList[index];
            console.log(this.getIndex);
        },
        fullname(firstname, lastname) {
            return `${firstname} ${lastname}`
        },
        average(math, physics, chemistry) {
            return (math + physics + chemistry) / 3
        },
        handleUpdate(index) {
            this.tableUpdate = !this.tableUpdate;
            // this.indexClass = this.classList[index];
            // console.log(this.indexClass);
            // this.classList[index]
            // console.log(this.classList);
            // this.fullNameUpdate = this.classList[index].fullname
            // console.log(this.classList[index].class);
            // this.fullNameUpdate = this.classList[index].fullname(firstname, lastname)
            // console.log(this.classList[index].firstname + this.classList[index].lastname);
            this.fullNameUpdate = this.classList[index].firstname + ' ' + this.classList[index].lastname
            this.classUpdate = this.classList[index].class
            this.scoreMath = this.classList[index].math
            this.scorePhysics = this.classList[index].physics
            this.scoreChemistry = this.classList[index].chemistry
        }
        // handleConfirm(this.indexClass) {

        // }
    },
}
</script>

<style scoped>
table,
th,
td {
    border-collapse: collapse;
    border: 1px solid black;
    padding: 10px;
}

.group-table td button {
    margin: 2px;
}

.group-update {
    border: 2px solid orange;
    border-radius: 10px;
    box-shadow: 5px 5px rgba(18, 30, 50, 0.7);
    display: flex;
    flex-direction: column;
    width: 500px;
    align-items: center;
    background-color: aqua;
}

.group-update h2 {
    color: red;
    margin-top: 10px;
}

.group-update .content-input {
    width: 80%;
    margin: 15px;
}

.group-update .group-input {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin: 0px;
}

.group-update .group-input input {
    width: 250px;
    padding: 5px;
}

.group-update .group-input p {
    font-size: larger;
    color: blue;
}

.group-update .group-button {
    margin-bottom: 10px;
}

.group-update .group-button button {
    padding: 8px;
    margin: 3px;

}
</style>