<template>
  <div>
    <div class="container">
      <div class="left">
        <h1 class="home-score">Home</h1>
        <div class="home-bg">
          <h1 class="score">{{ homePoints }}</h1>
        </div>
        <div class="increment-container">
          <div class="increment-number">
            <button class="increment-by" @click="incrementHomePoints(1)">
              + 1
            </button>
          </div>
          <div class="increment-number">
            <button class="increment-by" @click="incrementHomePoints(2)">
              + 2
            </button>
          </div>
          <div class="increment-number">
            <button class="increment-by" @click="incrementHomePoints(3)">
              + 3
            </button>
          </div>
        </div>
      </div>
      <div class="right">
        <h1 class="home-score">Guest</h1>
        <div class="home-bg">
          <h1 class="score">{{ GuestPoints }}</h1>
        </div>
        <div class="increment-container">
          <div class="increment-number">
            <button class="increment-by" @click="incrementGuestPoints(1)">
              + 1
            </button>
          </div>
          <div class="increment-number">
            <button class="increment-by" @click="incrementGuestPoints(2)">
              + 2
            </button>
          </div>
          <div class="increment-number">
            <button class="increment-by" @click="incrementGuestPoints(3)">
              + 3
            </button>
          </div>
        </div>
      </div>
    </div>

    <div class="new-game">
      <button @click="reset">New Game</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      homePoints: 0,
      GuestPoints: 0,
      leader: null
    };
  },
  watch: {
    homePoints(){
      const { homePoints } = this;
      const { GuestPoints } = this;
      if(homePoints > GuestPoints){
        this.leader = "Home Team is Leading"
      } this.leader = "Guest Team is Leading"
    }
  },
  methods: {
    incrementHomePoints(param) {
      this.homePoints += param;
    },
    incrementGuestPoints(param) {
      this.GuestPoints += param;
    },
    reset() {
      this.homePoints = 0;
      this.GuestPoints = 0;
    },
  },
};
</script>

<style scoped>
.container {
  display: flex;
  justify-content: center;
  gap: 106px;
  flex-wrap: wrap;
  margin-top: 180px;
}

.home-bg {
  background: #080001;
  border-radius: 5px;
  margin-top: 21px;
}

.home-score {
  font-family: "Nunito";
  font-style: normal;
  font-weight: 700;
  font-size: 40px;
  line-height: 36px;
  text-align: center;
  color: #eeeeee;
}

.score {
  font-style: normal;
  font-weight: 400;
  font-size: 90px;
  line-height: 127px;
  /* or 141% */
  text-align: center;
  color: #f94f6d;
}

.increment-container {
  display: flex;
  margin-top: 26px;
  gap: 10px;
}

.increment-number {
  border: 2px solid #9aabd8;
  border-radius: 5px;
}

.increment-by {
  font-style: normal;
  font-weight: 400;
  font-size: 18px;
  line-height: 28px;
  /* or 155% */
  text-align: center;
  color: #9aabd8;
  padding: 9px;
}

button {
  border: 2px solid #9aabd8;
  color: #fff;
}

button:hover {
  background: tomato;
}

.new-game{
  text-align: center;
  margin-top: 10px;
}
.new-game button {
  padding: 10px;
  background: #047857;
}
</style>
