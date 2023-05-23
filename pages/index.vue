<template>
    <div class="flex h-screen justify-center items-center bg-neutral-50 w-full p-2">
        <div class="md:min-w-[600px] sm:w-[400px] w-[350px] shadow-lg  m-auto p-4 bg-white rounded-md">
            <!-- heading -->
            <div class="flex justify-center items-center w-full flex-col border-b-[1px] pb-3 border-neutral-300 mb-4">
                <img src="/img/logo.svg" class="w-16 mb-4">
                <h1 class="text-2xl font-extrabold ">Pinia <span class="text-green-600">Task</span> Store </h1>
            </div>
            <!-- new task form -->
            <div>
                <TaskForm />
            </div>
            <!-- filter -->
            <div class="flex justify-center items-center mb-4">
                <button @click="filter = 'all'" class="py-2 px-4 bg-neutral-700 text-white rounded-l-md">All Tasks</button>
                <button @click="filter = 'favs'" class="py-2 px-4 bg-[#B01E28] text-white rounded-r-md">Fav Tasks</button>
            </div>
            <!-- task list -->
            <div>
                <div v-if="filter === 'all'">
                    <p class="mb-3 text-xl font-bold text-green-600">Your have {{ taskStore.totalCount }} Tasks Left To Do
                    </p>
                    <div v-for="task in taskStore.tasks">
                        <TaskDetails :task="task" />
                    </div>
                </div>
                <div v-if="filter === 'favs'">
                    <p class="mb-3 text-xl font-bold text-green-600 mt-4">Your have {{ taskStore.favCount }} Favs Left To Do
                    </p>
                    <div v-for="task in taskStore.favs">
                        <TaskDetails :task="task" />
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import { useTaskSore } from '@/store/counter'
export default {
    setup() {
        const taskStore = useTaskSore()
        const filter = ref('all')
        return {
            taskStore, filter
        }
    },
}

</script>

