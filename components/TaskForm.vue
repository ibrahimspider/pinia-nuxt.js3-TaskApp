<template>
    <div class="py-2 w-full mb-4">
        <form @submit.prevent="handleSubmit">
            <input class="p-2 border-[1px] w-[80%] border-neutral-400 rounded-l-md" type="text" placeholder="I Need To..." v-model="newTask">
            <button type="submit" class="bg-neutral-700 text-white p-[9px] w-[20%] rounded-r-md">Add</button>
        </form>
    </div>
</template>

<script>
import { useTaskSore } from '~/store/counter';
export default {
    setup() {
        const taskStore = useTaskSore();
        const newTask = ref("")

        const handleSubmit = () => {
            if (newTask.value.length > 0) {
                taskStore.addTask({
                    title: newTask.value,
                    isFav: false,
                    id: Math.floor(Math.random() * 10000)
                })
                newTask.value = ''
            }
        }
        return { handleSubmit, newTask }
    },
}
</script>
