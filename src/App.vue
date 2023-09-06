<template>
  <div >
    <h1 class="text01">เป่า...ยิง....ฉุบ!!!</h1>
    <br>
    <img v-if="! playing " src="https://i.pinimg.com/564x/b8/1b/ab/b81bab5ed41866eb9138adcc4e724780.jpg" alt="">
    </div>

  <div class="row row-cols-1 row-cols-md-2 g-4" v-if="playing">
  <div class="col">
    <div class="card">
      <img v-if="! playing " src="https://i.pinimg.com/564x/b8/1b/ab/b81bab5ed41866eb9138adcc4e724780.jpg" alt="" >
      <img :src="playerChoice" alt="Player One Choice" />
      <div class="card-body">
        <h4 class="text">playerOne</h4>
        <p>ScorePlayerOne:{{ scoreone }}</p>

        
      </div>
    </div>
  </div>
  <div class="col">
    <div class="card">
      <img v-if="! playing " src="https://i.pinimg.com/564x/b8/1b/ab/b81bab5ed41866eb9138adcc4e724780.jpg" alt="">
      <img :src="computerChoice" alt="Player Two Choice" />
      <div class="card-body">
        <h4 class="text">playerTwo</h4>
        <p>ScorePlayerTwo:{{ scoretwo }}</p>
        
      </div>
    </div>
  </div>
</div>

  <div>
    <br>
    <div class="text-center" v-if="playing" >
      <h3>RESELT:{{ result }}</h3>
    </div>
    
<br>
  <div class="row md-1">

    <div class="col md-2"><button @click="playGame" :disabled="gameOver">play</button></div>
    <div class="col md-2"><button @click="resetGame">restart</button></div>
   
  </div>
  </div>



</template>

<script>
export default {
  data() {
    return {
      scoreone: 0,
      scoretwo: 0,
      playing: false,
      playerChoice: "",
      computerChoice: "",
      result: "",
      gameOver: false,
      heartChoice: "https://i.pinimg.com/564x/93/21/ce/9321cef431c88def76bfd297f9930f32.jpg",
    };
  },
  methods: {
    playGame() {
      const choices = [
        "https://i.pinimg.com/564x/f8/0b/22/f80b2266564969c7463d3aad60a0a6c9.jpg",
        "https://i.pinimg.com/564x/dc/75/68/dc7568981848e28f2515083ce7b42603.jpg",
        "https://i.pinimg.com/564x/77/63/45/77634518bf48ce42e57d7f3e89e44e2e.jpg",
        "https://i.pinimg.com/564x/93/21/ce/9321cef431c88def76bfd297f9930f32.jpg"
      ];
      this.playerChoice = choices[Math.floor(Math.random() * choices.length)];
      this.computerChoice = choices[Math.floor(Math.random() * choices.length)];
      this.calculateResult();
      this.playing = true;
    },
    calculateResult() {
      if (this.playerChoice === this.computerChoice) {
        this.result = "เสมอ";
      } else if (this.playerChoice === "https://i.pinimg.com/564x/93/21/ce/9321cef431c88def76bfd297f9930f32.jpg") {
        this.result = "Player One ชนะ";
        this.scoreone += 1;
      } else if (this.computerChoice === "https://i.pinimg.com/564x/93/21/ce/9321cef431c88def76bfd297f9930f32.jpg") {
        this.result = "Player Two ชนะ";
        this.scoretwo += 1;
      }else if (
        (this.playerChoice === "https://i.pinimg.com/564x/f8/0b/22/f80b2266564969c7463d3aad60a0a6c9.jpg" && this.computerChoice === "https://i.pinimg.com/564x/77/63/45/77634518bf48ce42e57d7f3e89e44e2e.jpg") ||
        (this.playerChoice === "https://i.pinimg.com/564x/dc/75/68/dc7568981848e28f2515083ce7b42603.jpg" && this.computerChoice === "https://i.pinimg.com/564x/f8/0b/22/f80b2266564969c7463d3aad60a0a6c9.jpg") ||
        (this.playerChoice === "https://i.pinimg.com/564x/77/63/45/77634518bf48ce42e57d7f3e89e44e2e.jpg" && this.computerChoice === "https://i.pinimg.com/564x/dc/75/68/dc7568981848e28f2515083ce7b42603.jpg")
      ) {
        this.result = "Player One ชนะ";
        this.scoreone += 1;
      } else {
        this.result = "Player Two ชนะ";
        this.scoretwo += 1;
      }
    },
    resetGame() {
      this.playing = false;
      this.playerChoice = "";
      this.computerChoice = "";
      this.result = "";
      this.gameOver = false;
      this.scoreone = 0;
      this.scoretwo = 0;
    },

  },
};
</script>

<style scoped>

img {
  width: 200px; /* กำหนดความกว้างของรูปภาพ */
  height: 200px; /* กำหนดความสูงของรูปภาพ */
}

.flex-card {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
}
.text-center {
  text-align: center;
}
</style>
