<template>
  <div class="container">
    <div class="correctGreet" v-if="flag">
      <h1>Acertaste! <i class="fa-regular fa-face-smile smile"></i></h1>
    </div>
    <div class="incorrectGreet" v-if="!flag">
      <h2>Tenta outra vez mais tarde. <i class="fa-regular fa-face-frown sad"></i></h2>    
    </div>
    <div class="mainMessage">
      <h3>{{ msg }}</h3>
    </div>
    <div v-if="flag">
      <p class="dividing-line-cw">
        - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
      </p>
      <div class="footer">
        <p>Dirige-te à caixa UNICEF e retira um papel.</p> Boa sorte!
      </div>
      <p class="dividing-line-cw">
        - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
      </p>
    </div>

    <!-- To enable touch screen skip while touching anywhere -->
    <div class="bigHeight" v-if="!flag">
    </div>

  </div>
</template>

<script>
export default {
  name: 'CorrectWrong',
  props: {
    flag: Boolean,
    msg: String
  }
}
</script>

<style>

.container {
    font-size: 3rem;
    text-align: center;
    max-width: 1500px;
    margin-left: auto;
    margin-right: auto;
    margin-top: 0;
}
.correctGreet h1{
  position: relative;
  font-size: 6.5rem;
  height: 150px;
  top: -50px;
}
.incorrectGreet h2 {
  position: relative;
  font-size: 5.5rem;
  height: 150px;
  top: -50px;
}
.mainMessage {
  height: 400px;
}
.mainMessage h3 {
  font-weight: 400;
  font-size: 3.1rem;
}
.dividing-line-cw {
    font-size: 2.5rem;
    margin-top: 0;
    margin-bottom: 0;
}
.footer {
  font-weight: bold;
  margin-top: -10px;
  margin-bottom: -10px;
}
.bigHeight {
  height: 200px;
}
.smile {
  font-size: 11rem;
}
.sad {
  font-size: 11rem;
}

</style>
