<template>
    <button class="box" @click="emit('box-click', id)" :disabled="isTaken || isGameWon">
        {{ symbol }}
    </button>
</template>

<script setup lang="ts">
interface Props {
    isTaken: boolean
    symbol: 'X' | 'O' | "" 
    id: number
    isGameWon: boolean
}

const props = defineProps<Props>()
const emit = defineEmits(['box-click'])

</script>

<style scoped lang="scss">
.box{
    width: calc(400px / 4);
    height: calc(400px / 4);
    background-color: var(--bg-3);
    border-radius: 10px;
    color: white;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 72px;

}

</style>