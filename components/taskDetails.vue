<template>
    <div class="shadow-md py-2 px-3 rounded-md">
        <h3 class="text-lg mb-3 text-neutral-600 font-semibold">{{ task.title }}</h3>
        <div class="flex justify-between items-center">
            <i class="material-symbols-outlined text-neutral-500 cursor-pointer text-3xl"
                :class="task.isFav? 'text-[#B01E28]' : ''" @click="taskStore.toggleFav(task.id)">favorite </i>
            <i class="material-symbols-outlined text-neutral-500 cursor-pointer text-3xl"
                @click="taskStore.deleteTask(task.id)">delete </i>
        </div>
    </div>
</template>

<script>
import { useTaskSore } from '~/store/counter';

export default {
    props: ["task"],
    setup() {
        const taskStore = useTaskSore()

        return { taskStore }
    }
}
</script>

<style lang="scss" scoped></style>