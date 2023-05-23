<template>
    <div class="container">
        <!-- Heading -->
        <h2 class="text-center mt-5 bg-primary">Todo List App</h2>

        <!-- Input -->
        <div>
            <input type="text" v-model="task" placeholder="Write What you want....." class=" w-100 form-control" />
            <div class="btn1">
                <button class="btn btn-warning rounded-0 " @click="submitTask"> SUBMIT </button>
            </div>
        </div>

        <!-- Task table -->
        <table class="table table-bordered mt-5">
            <thead>
                <tr class="table_head">
                    <th scope="col">Tasks To Remember</th>
                    <th scope="col" class="text-center">Edit Task</th>
                    <th scope="col" class="text-center">Delete Task</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(task, index) in tasks" :key="index">
                    <td>
                        <span> {{ task.name }} </span>
                    </td>
                    <td class="text-center">
                        <div @click="editTask(index)"> <p class="fas fa-edit pointer"></p></div>
                    </td>
                    <td class="text-center">
                        <div @click="deleteTask(index)"> <span class="fa fa-trash pointer"></span> </div>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>
  
<script>
export default {
    name: "toDoApp",
    props: {
        msg: String,
    },

    data() {
        return {
            task: "",
            editedTask: null,
            tasks: [
                {
                    name: "Create YouTube video.",
                    status: "finished",
                },
            ],
        };
    },

    methods: {
        deleteTask(index) {
            this.tasks.splice(index, 1);
        },
        editTask(index) {
            this.task = this.tasks[index].name;
            this.editedTask = index;
        },
        submitTask() {
            if (this.task.length === 0) return;
            // update the task
            if (this.editedTask != null) {
                this.tasks[this.editedTask].name = this.task;
                this.editedTask = null;
            } else {
                // adding new task
                this.tasks.push({
                    name: this.task,
                    status: "todo",
                });
            }
            this.task = "";
        },
    },
};
</script>
<style scoped>
.container{
    max-width: 50%;
    background-color: rgb(236, 230, 230);
}
.pointer {
    cursor: pointer;
}
.table_head{
    background-color: antiquewhite;
}
.btn1{
    margin: 10px;
}


.line-through {
    text-decoration: line-through;
}
</style>