<template>
    <section>
        <h2 class="p-6 text-3xl font-bold text-center">List of Todo</h2>
        <ul class="">
            <TaskItem @removeTask="removeTodo" @toggleTask="toggleCheckbox" v-for="task in taskList" :id="task.id"
                :key="task.id" :name="task.taskName" :isFinished="task.isFinished" />
        </ul>
    </section>
</template>
<script setup>
import { useTodo } from '@/store/TodoStore';
const { taskList } = useTodo()
import TaskItem from './TaskItem.vue';

const emit = defineEmits(['toggleTask', 'removeTask'])

const toggleCheckbox = (payload) => {
    emit('toggleTask', payload)
}
const removeTodo = (payload) => {
    emit('removeTask', payload)
}
</script>