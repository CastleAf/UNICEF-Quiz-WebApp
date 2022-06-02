<script setup>

import { ref, computed } from 'vue'
const questions = ref([
  {
	question: 'Quando tenho de pedir ajuda é sinal de que:',
	answer: 2,
	options: [
		'sou fraco e não consigo fazer as coisas sozinho',
		'os outros são melhores do que eu',
		'todos precisamos de ajuda em algum momento e reconhecer isso é um sinal de força'
	],
	selected: null
  },
  {
	question: 'Quando me sinto muito ansioso, eu:',
	answer: 1,
	options: [
		'devo ignorar, porque não tem importância ',
		'devo falar com alguém sobre o que sinto, para que me possam ajudar',
		'devo ficar sozinho e esperar que passe'
	],
	selected: null
  },
  {
	question: 'Todas as nossas emoções são importantes!',
	answer: 0,
	options: [
		'verdadeiro, todas as emoções são necessárias e dão-nos informação sobre o que se passa connosco',
		'falso, só algumas emoções são importantes',
		'falso, só são importantes as emoções positivas',
    'verdadeiro, mas devemos ignorar as emoções negativas'
	],
	selected: null
  },
  {
	question: 'Estou no recreio com os meus amigos e sou o único que quer jogar um jogo. O que posso fazer?',
	answer: 2,
	options: [
		'ignoro a opinião dos meus amigos e obrigo-os a fazerem o que eu quero',
		'afasto-me deles e vou procurar outros amigos que façam o que eu quero',
		'ouvimos a opinião uns dos outros e, em equipa, decidimos o que fazer',
    'não digo nada porque a minha opinião não importa e faço o que eles quiserem'
	],
	selected: null
  },
  {
	question: 'A solidão é uma emoção que faz parte da adolescência. Concordas?',
	answer: 1,
	options: [
		'não concordo: a solidão é uma emoção negativa que nos faz sentir mal e tento evitá-la sempre que posso',
		'concordo: todos podemos sentirmo-nos sós, até mesmo quando rodeado de outras pessoas',
		'não concordo: só sente solidão quem não tem amigos '
	],
	selected: null
  },
  {
	question: 'Quero muito aprender a andar de skate, mas estou sempre a cair. Qual é a minha reação?',
	answer: 0,
	options: [
		'continuo até conseguir, não sou de desistir, e acredito que vai valer a pena',
		'desisto e vou andar de bicicleta que já sei andar muito bem',
		'fico chateado e coloco as culpas no meu skate',
	],
	selected: null
  },
  {
	question: 'O que penso em relação ao mundo?',
	answer: 3,
	options: [
		'está cheio de pessoas más, perigosas, que tentam aproveitar-se das pessoas',
		'está cheio de pessoas boas, que nos querem ajudar',
		'acho que tem mais pessoas boas do que más',
    'acho que o mundo é feito de muitas pessoas diferentes e é preciso conhecê-las para saber se são boas ou más'
	],
	selected: null
  },
  {
	question: 'Convidaste um/a amigo/a a ir à praia contigo mas ele/a não se sente totalmente confortável com o seu corpo. O que achas que ele/a deve fazer?',
	answer: 0,
	options: [
		'inventar uma desculpa e não aparecer',
		'tentar convencer-te que não é uma boa ideia e que deviam fazer outra coisa',
		'deve ir, sem pensar muito nisso e tentando aceitar como é'
	],
	selected: null
  },
  {
	question: 'Reparaste que um/a amigo/a precisa de ajuda. O que deves fazer?',
	answer: 2,
	options: [
		'ignorar. Todos temos os nossos maus momentos e aquilo deve passar',
		'falar com um adulto e dizer para o/a ajudarem',
		'falar com esse amigo/a, ouvir e se necessário, pedir ajuda a um adulto de confiança '
	],
	selected: null
  },
  {
	question: 'Alguém partilhou uma fotografia de um/a amigo/a nas redes sociais sem a sua autorização. Qual é a tua reação?',
	answer: 0,
	options: [
		'avisar o/a minha/a amiga/o e pedir a quem partilhou para eliminar. Devemos respeitar a privacidade uns dos outros',
		'não fazer nada. Já se sabe que nas redes sociais tudo pode acontecer!',
		'partilhar essa fotografia com outras pessoas, porque agora é publico'
	],
	selected: null
  }
])


let quizStart = ref(true)
const quizCompleted = ref(false)
let currentQuestion = ref(0)
const score = computed(() => {
	let value = 0
	questions.value.map(q => {
		if (q.selected != null && q.answer == q.selected) {
			console.log('correct');
			value++
		}
	})
	return value
})
const getCurrentQuestion = computed(() => {
	let question = questions.value[currentQuestion.value]
	question.index = currentQuestion.value
	return question
})
const SetAnswer = (e) => {
	questions.value[currentQuestion.value].selected = e.target.value
	e.target.value = null
}
const NextQuestion = () => {
	if (currentQuestion.value < questions.value.length - 1) {
		currentQuestion.value++
		return
	}
	
  // TODO: Fix restarting quiz
  // currentQuestion = ref(0)
	// quizStart.value = true
  window.location.reload()

}

const handleClick = () => {
  quizStart.value = false
}
</script>

<template>
	<main class="app">
    <div v-if="quizStart" class="border-header">
      <h1>Quiz UNICEF</h1>
    </div>
    
    <section class="landing" v-if="quizStart">
      <h2>Bem-vindo/a</h2>
   
      <div class="explain-text">
        <p>
          Como sabes, o desporto é muito importante para o teu bem-estar físico e psicológico. 
          Sabemos que tens o talento... <b>Mas sabes cuidar da tua mente?</b>
        </p>
        <p class="dividing-line">
          - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
        </p>
        <div class="flex-box">
          <p class="left-text">
            <b>Acerta na resposta à pergunta que se segue e ganha o teu prémio.</b>
          </p>
          <button @click="handleClick">Jogar</button>
        </div>
        <p class="dividing-line">
          - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
        </p>

        <div class="flex-container">
          <flex-item class="tiny-text">Uma ação:</flex-item>
          <flex-item class="tiny-text">Em colaboração com:</flex-item>
          <flex-item></flex-item>
        </div>
        <div class="flex-container">
          <flex-item class="unicef-logo">
            <img class="unicef" alt="UNICEF Logo" src="./assets/logo-UNICEF.png">
          </flex-item>
          <flex-item>
            <img class="nlh" alt="NLH Logo" src="./assets/Untitled2.png">
          </flex-item>
          <flex-item>
            <img class="eu" src="./assets/Untitled.png">
          </flex-item>
        </div>
      </div>
    </section>
		
    <div v-if="!quizCompleted && !quizStart" class="border-header-quiz">
      <h3>Quiz UNICEF</h3>
    </div>
		<section class="quiz" v-if="!quizCompleted && !quizStart">
			<div class="quiz-info">
				<span class="question">{{ getCurrentQuestion.question }}</span>
			</div>
			
			<div class="options">
				<label 
					v-for="(option, index) in getCurrentQuestion.options"
          :key="option.id" 
					:for="'option' + index"
					:class="`option ${
						getCurrentQuestion.selected == index 
							? index == getCurrentQuestion.answer 
								? 'correct' 
								: 'wrong'
							: ''
					} ${
						getCurrentQuestion.selected != null &&
						index != getCurrentQuestion.selected
							? 'disabled'
							: ''
					}`">
					<input 
						type="radio" 
						:id="'option' + index" 
						:name="getCurrentQuestion.index" 
						:value="index" 
						v-model="getCurrentQuestion.selected" 
						:disabled="getCurrentQuestion.selected"
						@change="SetAnswer" 
					/>
          <div class="flex-container">
            <span class="option-letter" v-if="index == 0"> A)</span>
            <span class="option-letter" v-if="index == 1"> B)</span>
            <span class="option-letter" v-if="index == 2"> C)</span>
            <span class="option-letter" v-if="index == 3"> D)</span>      
            <span class="option-content">{{ option }}</span>
            <span></span>
          </div>
				</label>
			</div>
			
			<button 
				@click="NextQuestion" 
				:disabled="!getCurrentQuestion.selected">
				{{ 
					getCurrentQuestion.index == questions.length - 1 
						? 'Terminar Quiz' 
						: getCurrentQuestion.selected == null
							? 'Seleciona uma opção'
							: 'Próxima pergunta'
				}}
			</button>
		</section>

    <!-- TODO: Remove score if not needed -->
		<section v-if="quizCompleted">
			<h2>You have finished the quiz!</h2>
			<p>Your score is {{ score }}/{{ questions.length }}</p>
		</section>
	</main>
</template>

<style>
@font-face {
    font-family: 'Univers';
    src: url('./assets/fonts/Univers.woff2') format('woff2'),
        url('./assets/fonts/Univers.woff') format('woff');
    font-weight: normal;
    font-style: normal;
    font-display: swap;
}
@font-face {
    font-family: 'Univers-bold';
    src: url('./assets/fonts/Univers-bold.woff2') format('woff2'),
         url('./assets/fonts/Univers-bold.woff') format('woff');
    font-weight: normal;
    font-style: normal;

}
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: "Univers", sans-serif;
}
body {
    background-color: #1cabe2;
    color: #fff;
}
.app {
    display: flex;
    flex-direction: column;
    align-items: center;
    height: 100vh;
}
h1 {
    font-size: 5rem;
    padding: 20px;
}
h2 {
    font-size: 4.5rem;
    text-align: center;
}
h3 {
  font-size: 3rem;
  padding: 20px;
}
.border-header {
    border-radius: 25px;
    background-color: white;
    color: #1cabe2;
    padding-left: 100px;
    padding-right: 100px;
    padding-top: 50px;
    margin-bottom: 50px;
    margin-top: -20px;
}
.border-header-quiz {
    border-radius: 25px;
    background-color: white;
    color: #1cabe2;
    padding-left: 50px;
    padding-right: 50px;
    padding-top: 20px;
    margin-bottom: 50px;
    margin-top: -20px;
}
.explain-text {
    font-size: 3.5rem;
    text-align: center;
    max-width: 70%;
    margin-left: auto;
    margin-right: auto;
    margin-top: 0;
}
.dividing-line {
    font-size: 2.5rem;
    margin-top: 1rem;
    margin-bottom: 1rem;
}
.flex-box {
    display: flex;
    justify-content: space-between;
}
.flex-container {
    display: flex;
    justify-content: space-between;
}
flex-container::before {
  content: "";
}
flex-container::after {
  content: "";
}
flex-item {
  height: 50px;
  width: 350px;
  margin-left: -30px;
  margin-top: 0;
}
.left-text {
    font-size: 2.5rem;
    margin-left: 100px;
    width: 700px;
    text-align: left;
}
button {
    appearance: none;
    outline: none;
    border: none;
    cursor: pointer;
    padding-left: 4rem;
    padding-right: 4rem;
    background-color: #ffffff;
    color: #1cabe2;
    font-weight: bold;
    font-size: 4rem;
    border-radius: 2.5rem;
    margin-right: 100px;
}
button:disabled {
    opacity: 0.5;
}

.quiz {
    font-size: 3rem;
    text-align: center;
    max-width: 1500px;
    margin-left: auto;
    margin-right: auto;
    margin-top: 0;
}
.quiz-info {
    text-align: center;
    width: 1500px;
    height: 140px;
    margin: auto;
    margin-bottom: 2rem;
}

.options {
    margin-bottom: 1rem;
    width: 100%;
    font-size: 2rem;
    font-weight: bold;
    color: #1cabe2;
}
.option {
    padding: 1.25rem;
    display: block;
    background-color: #fff;
    margin-bottom: 1.5rem;
    border-radius: 2rem;
    height: 100px;
    cursor: pointer;
}
.option:hover,
button:hover {
    background-color: #ececec;
}
.option-container {
  display: flex;
}
.option-letter {
  text-align: right;
}
.option-content {
  max-width: 1350px;
}

.tiny-text {
  font-size: 1.3rem;
  text-align: left;
}
.tiniest-text {
  font-size: 0.5rem;
}
.unicef {
  width: 350px;
}
.nlh {
  width: 380px;
}
.unicef-logo {
  margin-left: -50px;
}
.eu {
  width: 600px;
  margin-left: -50px;
}




.option.correct {
    background-color: #2cce7d;
}
.option.wrong {
    background-color: #ff5a5f;
}
.option:last-of-type {
    margin-bottom: 0;
}
.option.disabled {
    opacity: 0.5;
}
.option input {
    display: none;
}
</style>