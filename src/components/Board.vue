<template>
  <div class="game">
    <div class="game__board">
      <Box 
        v-for="(x, i) in boxList"
        :key="i"
        :isTaken="x.isTaken"
        :symbol="x.symbol"
        :id="x.id"
        @box-click="handleBoxClick"
        :isGameWon="isGameWon"
      />
    </div>
    <div 
      class="game__end" 
      v-if="winner === 'P1' || winner ==='P2'"
    >
      <p >{{ winner }} WON !!!</p>
      <button @click="handleRestart" class="game__btn-restart">RESTART</button>
    </div>
  </div>
</template>

<script setup lang="ts">
import { computed, ref, onMounted } from 'vue';
import Box from './Box.vue'
interface IBox {
  isTaken: boolean
  symbol: 'X' | 'O' | ""
  id: number
}

const boxList = ref<IBox[]>([])
const nextSymbol = computed<'X' | 'O'>(() => {
  if(boxList.value.filter((item) => item.isTaken === false).length % 2 === 0) {
    return 'O'
  } else {
    return 'X'
  }
})

const winner = computed<'P1' | 'P2' | "">(() => {
  if(boxList.value.length <= 1) return ""

  const checkWinner = (s: 'O' | 'X') => {
    for (let i = 0; i < 3; i++) {
      if (boxList.value[i].symbol === s && boxList.value[i+3].symbol === s && boxList.value[i+6].symbol === s ||
          boxList.value[i*3].symbol === s && boxList.value[(i*3)+1].symbol === s && boxList.value[(i*3)+2].symbol === s) {
            return s === 'O' ?  "P1" : "P2"
      }
    }
    for (let i = 1; i <= 2; i++) {
      if (boxList.value[(i-1)*2].symbol === s && boxList.value[4].symbol === s && boxList.value[10 - (i*2)].symbol === s){
        return s === 'O' ? "P1" : "P2"
      }
    }
    return ""
  }


  return checkWinner('O') || checkWinner('X')
})

const isGameWon = computed<boolean>(() => {
  if(winner.value === 'P1' || winner.value === 'P2') {
    return true
  }
  return false
})

const handleBoxClick = (id: number) => {
  if(!boxList.value[id].isTaken) {
    boxList.value[id].isTaken = true
    boxList.value[id].symbol = nextSymbol.value
  }
}

const handleRestart = () => {
  boxList.value = []
  fillBoxList()
}

const fillBoxList = () => {
  for (let i = 0; i < 9; i++) {
    boxList.value.push({
      isTaken: false,
      id: i,
      symbol: ""
    })
    
  }
}

onMounted(() => {
  fillBoxList()
})

</script>

<style scoped lang="scss">

.game {
  &__board {
    box-sizing: border-box;
    height: 400px;
    width: 400px;
    background-color: var(--bg-2);
    border-radius: 10px;
    padding: 25px;
    
    display: flex;
    flex-wrap: wrap;
    gap: 25px;
  }

  &__end {
    font-size: 36px;  
    display: flex;
    flex-direction: column;
    align-items: center;

  }

  &__btn-restart {
    font-size: 24px;
    color: white;
    border: none;
    padding: 15px;
    border-radius: 10px;
    background-color: var(--bg-3);

    &:hover {
      cursor: pointer;
      background-color: var(--bg-2);
    }

  }
}

</style>