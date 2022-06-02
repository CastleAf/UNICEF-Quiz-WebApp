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
const currentQuestion = ref(0)
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
	
	quizCompleted.value = true
}

const handleClick = () => {
  quizStart.value = false
}
</script>

<template>
	<main class="app">
    <div class="border-header">
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
          <div class="unicef" min-width="900px">79318923789127381297389127</div>
          <div class="nextLevelHub">2</div>
          <div class="eu">3</div>
        </div>
      </div>
    </section>
		
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
          <div class="option-row">
            <span class="option-letter mt-2" v-if="index == 0"> A)</span>
            <span class="option-letter" v-if="index == 1"> B)</span>
            <span class="option-letter" v-if="index == 2"> C)</span>
            <span class="option-letter" v-if="index == 3"> D)</span>      
            <span>{{ option }}</span>
          </div>
				</label>
			</div>
			
			<button 
				@click="NextQuestion" 
				:disabled="!getCurrentQuestion.selected">
				{{ 
					getCurrentQuestion.index == questions.length - 1 
						? 'Finish' 
						: getCurrentQuestion.selected == null
							? 'Select an option'
							: 'Next question'
				}}
			</button>
		</section>

		<section v-if="quizCompleted">
			<h2>You have finished the quiz!</h2>
			<p>Your score is {{ score }}/{{ questions.length }}</p>
		</section>
	</main>
</template>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: "Montserrat", sans-serif;
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
.border-header {
    font-family: consolas;
    border-radius: 25px;
    background-color: white;
    color: #1cabe2;
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
    flex-wrap: nowrap;
}
.left-text {
    font-size: 3rem;
    margin-left: 100px;
    width: 790px;
}
button {
    appearance: none;
    outline: none;
    border: none;
    cursor: pointer;
    padding-left: 1rem;
    padding-right: 1rem;
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
    font-size: 3.5rem;
    text-align: center;
    max-width: 70%;
    margin-left: auto;
    margin-right: auto;
    margin-top: 0;
}
.quiz-info {
    max-width: 60%;
    margin: auto;
    margin-bottom: 3rem;
}

.options {
    margin-bottom: 1rem;
    font-size: 2rem;
    font-weight: bold;
    color: #1cabe2;
}
.option {
    padding: 1rem;
    display: block;
    background-color: #fff;
    margin-bottom: 0.5rem;
    border-radius: 2rem;
    height: 100px;
    cursor: pointer;
}
.option:hover,
button:hover {
    background-color: #ececec;
}
.option-letter {
  text-align: left;
  margin-left: 10px;
  margin-right: 30px;
}
.option-row {
  display: flex;
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

h2 {
    font-size: 4.5rem;
    text-align: center;
}
</style>