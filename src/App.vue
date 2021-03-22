<template>
  <div class="app">
    <h1>Tic Tac Toe</h1>
    <p>{{player}}</p>
    <p>{{msg}}</p>
    <div class="container">
      
      <box 
      class="box" 
      v-for="num in list" 
      :key="num"
      :boxNum='num'
      :round='round'
      @boxClicked='doThis'
      >
      </box>

    </div>
  </div>
</template>

<script>
import box from './components/Box'

export default {
  name: 'App',
  components: {
    box
  },

  data: function(){
    return {
      msg: '',
      list: [0, 1, 2, 3, 4, 5, 6, 7, 8],
      round: 1,
      player: "player 1's turn",
      player1Clicks: [],
      player2Clicks: []
    }
  },

  methods:{
    doThis: function(boxNum){
      this.round += 1
      if(this.round%2 === 0){
        this.player = "player 2's turn"
        this.player1Clicks.push(boxNum)
        this.winConP1()
        

      }
      else{
        this.player = "player 1's turn"
        this.player2Clicks.push(boxNum)
        this.winConP2()
      }
      
      if(this.round === 10){
        this.msg = 'IT IS A DRAW'
      }

    },

    // WIN CODITION FOR PLAYER1
    winConP1: function(){
      if(this.player1Clicks.includes(0) 
      && this.player1Clicks.includes(1) 
      && this.player1Clicks.includes(2))
      {
        this.msg = 'PLAYER 1 Won'
      }
      else if (this.player1Clicks.includes(3) 
      && this.player1Clicks.includes(4) 
      && this.player1Clicks.includes(5))
      {
        this.msg = 'PLAYER 1 Won'
      }
      else if (this.player1Clicks.includes(6) 
      && this.player1Clicks.includes(7) 
      && this.player1Clicks.includes(8))
      {
        this.msg = 'PLAYER 1 Won'
      }


      else if (this.player1Clicks.includes(0) 
      && this.player1Clicks.includes(3) 
      && this.player1Clicks.includes(6))
      {
        this.msg = 'PLAYER 1 Won'
      }
      else if (this.player1Clicks.includes(1) 
      && this.player1Clicks.includes(4) 
      && this.player1Clicks.includes(7))
      {
        this.msg = 'PLAYER 1 Won'
      }
      else if (this.player1Clicks.includes(2) 
      && this.player1Clicks.includes(5) 
      && this.player1Clicks.includes(8))
      {
        this.msg = 'PLAYER 1 Won'
      }


      else if (this.player1Clicks.includes(0) 
      && this.player1Clicks.includes(4) 
      && this.player1Clicks.includes(8))
      {
        this.msg = 'PLAYER 1 Won'
      }
      else if (this.player1Clicks.includes(2) 
      && this.player1Clicks.includes(4) 
      && this.player1Clicks.includes(6))
      {
        this.msg = 'PLAYER 1 Won'
      }
    },


    // WIN CONDITION FOR PLAYER 2
    winConP2: function(){
      if(this.player2Clicks.includes(0) 
      && this.player2Clicks.includes(1) 
      && this.player2Clicks.includes(2))
      {
        this.msg = 'PLAYER 2 Won'
      }
      else if (this.player2Clicks.includes(3) 
      && this.player2Clicks.includes(4) 
      && this.player2Clicks.includes(5))
      {
        this.msg = 'PLAYER 2 Won'
      }
      else if (this.player2Clicks.includes(6) 
      && this.player2Clicks.includes(7) 
      && this.player2Clicks.includes(8))
      {
        this.msg = 'PLAYER 2 Won'
      }


      else if (this.player2Clicks.includes(0) 
      && this.player2Clicks.includes(3) 
      && this.player2Clicks.includes(6))
      {
        this.msg = 'PLAYER 2 Won'
      }
      else if (this.player2Clicks.includes(1) 
      && this.player2Clicks.includes(4) 
      && this.player2Clicks.includes(7))
      {
        this.msg = 'PLAYER 2 Won'
      }
      else if (this.player2Clicks.includes(2) 
      && this.player2Clicks.includes(5) 
      && this.player2Clicks.includes(8))
      {
        this.msg = 'PLAYER 2 Won'
      }


      else if (this.player2Clicks.includes(0) 
      && this.player2Clicks.includes(4) 
      && this.player2Clicks.includes(8))
      {
        this.msg = 'PLAYER 2 Won'
      }
      else if (this.player2Clicks.includes(2) 
      && this.player2Clicks.includes(4) 
      && this.player2Clicks.includes(6))
      {
        this.msg = 'PLAYER 2 Won'
      }
    }
  }

}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Quicksand:wght@600&display=swap');
  
  .app{
    font-family: 'Quicksand', sans-serif;
    text-align: center;
  }
  .container{
    width: 340px;
    height: 330px;
    background-color: #F2C078;

    padding-top: 10px;
    margin-left: auto;
    margin-right: auto;

    border-radius: 5px;

    display: grid;
    grid-template-columns: repeat(3, 100px);
    grid-template-rows: repeat(3, 100px);
    row-gap: 10px;
    column-gap: 10px;

    text-align: center;
    justify-content: center;
    align-items: center;
  }

  .box{
    width: 100%;
    height: 100%;
    background-color: #FAEDCA;

    border-radius: 5px;

    display: flex;
    justify-content: center;
    align-items: center;
  }
 
</style>
