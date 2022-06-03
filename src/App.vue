<script setup>
import { ref, computed } from 'vue'
import CorrectWrong from './components/CorrectWrong.vue';

const questions = ref([
  {
	question: 'Quando tenho de pedir ajuda é sinal de que:',
	answer: 2,
	options: [
		'sou fraco e não consigo fazer as coisas sozinho',
		'os outros são melhores do que eu',
		'todos precisamos de ajuda em algum momento e reconhecer isso é um sinal de força'
	],
	selected: null,
  correct: 'Às vezes, podemos sentir-nos tristes, preocupados, ansiosos ou sem esperança. Estes pensamentos não são raros e não deves sentir vergonha se os tiveres. E lembra-te que não estás sozinho/a, há pessoas que te podem ajudar.',
  wrong: 'Nem sempre é fácil controlar a ansiedade, a preocupação ou a tristeza, mas isso não significa que não estás a conseguir lidar com a situação. Falar com um amigo, pai, mãe, professor, adulto de confiança sobre como te estás a sentir, é um ato de coragem e poderá ajudar-te.'
  },
  {
	question: 'Quando me sinto muito ansioso, eu:',
	answer: 1,
	options: [
		'devo ignorar, porque não tem importância ',
		'devo falar com alguém sobre o que sinto, para que me possam ajudar',
		'devo ficar sozinho e esperar que passe'
	],
	selected: null,
  correct: 'É importante que compreendas como te sentes. Não ignores os teus sentimentos. E lembra-te que as pessoas em quem confias te podem ajudar.',
  wrong: 'É normal sentires o que sentes. Obrigares-te a estar sempre “feliz”, “positivo" ou “produtivo” pode fazer-te sentir pior. Saber lidar com os desafios é aprender a pensar ativamente sobre eles e conversar com alguém em quem confiamos sobre como nos sentimos e quais as melhores formas de lidar com a situação.'
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
	selected: null,
  correct: 'Cada pessoa interpreta o que se passa à sua volta de forma diferente e isso tem impacto na maneira como nos sentimos e comportamos. Reconhecer, expressar e lidar com as emoções contribui para o nosso desenvolvimento emocional.',
  wrong: 'Todas as emoções, quer sejam positivas ou negativas, têm uma função. Todas dão-nos informações importantes que nos fazem crescer.'
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
	selected: null,
  correct: 'É importante respeitarmos os interesses, a vontade e os gostos de cada pessoa. Podemos ser diferentes e mesmo assim encontrar pontos em comum. Já pensaste que também pode ser uma oportunidade para aprenderes com os outros?',
  wrong: 'É importante respeitarmos as outras pessoas como são, com gostos e interesses diferentes dos nossos. O diálogo e a colaboração ajudam-nos a encontrarmos soluções em grupo e a identificarmos pontos em comum que não sabíamos que tínhamos com as outras pessoas.'
  },
  {
	question: 'A solidão é uma emoção que faz parte da adolescência. Concordas?',
	answer: 1,
	options: [
		'não concordo: a solidão é uma emoção negativa que nos faz sentir mal e tento evitá-la sempre que posso',
		'concordo: todos podemos sentirmo-nos sós, até mesmo quando rodeado de outras pessoas',
		'não concordo: só sente solidão quem não tem amigos '
	],
	selected: null,
  correct: 'Todos nós podemos passar por situações ou fases em que nos sentimos sozinhos, mesmo com tantas pessoas à nossa volta. É importante estarmos atentos ao que sentimos e mantermos o contacto com a família e com os amigos em quem confiamos.',
  wrong: 'Os adolescentes que enfrentam mudanças no dia-a-dia, apesar de estarem acompanhados, podem sentir-se sozinhos e desmotivados. Se alguma vez te sentires sozinho, conversa com um/a amigo/a, a tua família, ou alguém em quem confies.'
  },
  {
	question: 'Quero muito aprender a andar de skate, mas estou sempre a cair. Qual é a minha reação?',
	answer: 0,
	options: [
		'continuo até conseguir, não sou de desistir, e acredito que vai valer a pena',
		'desisto e vou andar de bicicleta que já sei andar muito bem',
		'fico chateado e coloco as culpas no meu skate',
	],
	selected: null,
  correct: 'Cada pessoa não é as suas circunstâncias, não é aquilo que lhe acontece. Podemos sempre uma escolher o que queremos fazer com o que nos acontece. Já ouviste falar no termo “Resiliência”? É a capacidade de enfrentar as dificuldades de uma forma boa, aprender a ser mais tolerante (aceitar certas falhas ou erros) e flexível (adaptar às situações).',
  wrong: 'Nem sempre as coisas correm como gostaríamos. É importante trabalharmos a nossa capacidade de transformar os obstáculos em oportunidades. A questão é sempre o que cada um faz com as dificuldades que enfrenta: se queremos focar-nos na frustração ou transformá-la em motivação.'
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
	selected: null,
  correct: 'Quando olhamos para uma pessoa (seja uma pessoa próxima ou uma pessoa que não conhecemos), é importante lembrarmo-nos que ela é muito mais do que aparenta ser. É preciso conhecer quem a pessoa é de verdade.',
  wrong: 'Quando olhamos para uma pessoa (seja uma pessoa próxima ou uma pessoa que não conhecemos), é importante lembrarmo-nos que ela é muito mais do que aparenta ser. É preciso conhecer quem a pessoa é de verdade.'
  },
  {
	question: 'Convidaste um/a amigo/a a ir à praia contigo mas ele/a não se sente totalmente confortável com o seu corpo. O que achas que ele/a deve fazer?',
	answer: 2,
	options: [
		'inventar uma desculpa e não aparecer',
		'tentar convencer-te que não é uma boa ideia e que deviam fazer outra coisa',
		'deve ir, sem pensar muito nisso e tentando aceitar como é'
	],
	selected: null,
  correct: 'Todos nós somos diferentes e também temos formas diferentes de lidar com o nosso corpo e com a nossa aparência. Aprendermos a aceitarmo-nos tal como somos, ajuda-nos a sentirmo-nos melhor e mais felizes. Uma dica: nestas situações, pensa em algo que possas dizer a ti mesmo e que funcione como um incentivo.',
  wrong: 'Todos nós somos diferentes e também temos formas diferentes de lidar com o nosso corpo e com a nossa aparência. É muito importante trabalharmos a capacidade de nos conhecermos e desenvolvermos um sentimento de empatia connosco próprios e com os outros à nossa volta, tornando-nos mais capazes de nos aceitarmos a nós mesmos e aos outros tal como são.'
  },
  {
	question: 'Reparaste que um/a amigo/a precisa de ajuda. O que deves fazer?',
	answer: 2,
	options: [
		'ignorar. Todos temos os nossos maus momentos e aquilo deve passar',
		'falar com um adulto e dizer para o/a ajudarem',
		'falar com esse amigo/a, ouvir e se necessário, pedir ajuda a um adulto de confiança '
	],
	selected: null,
  correct: 'Pode acontecer perceberes que alguém de quem gostas ou conheces não está bem e precisa de ajuda. Perguntares como é que podes ajudar, demonstrar que te importas, poderá fazer toda a diferença para essa pessoa. Se a pessoa estiver em perigo, não tentes resolver a situação sozinho/a, pede ajuda a um adulto de confiança.',
  wrong: 'Se perceberes que um/a amigo/a precisa de ajuda, fala com ele/a e tenta oferecer apoio. Não fazer nada pode deixar a pessoa a sentir que todos estão contra ele ou que ninguém se importa. As tuas palavras podem fazer a diferença. Se a pessoa estiver em perigo, não tentes resolver a situação sozinho/a, pede ajuda a um adulto de confiança.'
  },
  {
	question: 'Alguém partilhou uma fotografia de um/a amigo/a nas redes sociais sem a sua autorização. Qual é a tua reação?',
	answer: 0,
	options: [
		'avisar o/a minha/a amiga/o e pedir a quem partilhou para eliminar. Devemos respeitar a privacidade uns dos outros',
		'não fazer nada. Já se sabe que nas redes sociais tudo pode acontecer!',
		'partilhar essa fotografia com outras pessoas, porque agora é publico'
	],
	selected: null,
  correct: 'A privacidade é um direito que todas as pessoas têm e deve ser respeitado. Agora, mais do que nunca, precisamos de refletir sobre o que partilhamos ou dizemos e sobre a forma como isso pode prejudicar os outros. Vamos criar uma comunidade online mais forte e segura. Está nas nossas mãos!',
  wrong: 'A privacidade é um direito que todas as pessoas têm e deve ser respeitado. É importante pensarmos duas vezes antes de escrever ou publicar conteúdos online que poderão ficar para sempre disponíveis. Podem vir a magoar-te ou a magoar outras pessoas. Vamos criar uma comunidade online mais forte e segura. Está nas nossas mãos!'
  }
])

const correctWrongScreen = ref(false)
const correctWrongAnswer = ref(true)
const correctWrongText = computed(() => {
	let text = ""
  let q = questions.value[currentQuestion.value]

  if (q.selected != null && q.answer == q.selected) {
    text = q.correct
  }
  else {
    text = q.wrong
  }
	return text
})

const quizStart = ref(true)
const currentQuestion = ref(0)
const quizOver = ref(false)

const getCurrentQuestion = computed(() => {
	let question = questions.value[currentQuestion.value]
	question.index = currentQuestion.value
	return question
})
const SetAnswer = (e) => {
	questions.value[currentQuestion.value].selected = e.target.value
	e.target.value = null

  goToCorrectWrongScreen(e.path[1].classList[1])
}
const goToCorrectWrongScreen = (q) => {
  if (q == "correct") { correctWrongAnswer.value = true }
  else { correctWrongAnswer.value = false }

  correctWrongScreen.value = true
}
const NextQuestion = () => {
  correctWrongScreen.value = false
	if (currentQuestion.value < questions.value.length - 1) {
		currentQuestion.value++
		return
	}
  quizOver.value = true
  window.location.reload()

}
const handleClick = () => {
  quizStart.value = false
}
const refresh = () => {
  window.location.reload()
}

// Timeout -> Restart quiz when idle for 1 minute
var inactivityTime = function () {
  var time;
  window.onload = resetTimer;
  // DOM Events
  document.onmousemove = resetTimer;
  document.onkeydown = resetTimer;

  function logout() {
    window.location.reload()
  }

  function resetTimer() {
    clearTimeout(time);
    time = setTimeout(logout, 45000)
    }
};
window.onload = function() {
  inactivityTime();
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
		
    <div v-if="!quizStart" class="border-header-quiz">
      <h3>Quiz UNICEF</h3>
    </div>
		<section class="quiz" v-if="!correctWrongScreen && !quizStart && !quizOver">
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
		</section>

		<section v-if="correctWrongScreen" @click="NextQuestion">
      <CorrectWrong :flag="correctWrongAnswer" :msg="correctWrongText"></CorrectWrong>
		</section>
    <div v-if="!quizStart" class="fixedHouseButton">
      <i @click="refresh" class="fa-solid fa-house house"></i>
    </div>
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
    border-radius: 3rem;
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
.fixedHouseButton {
  position: fixed;
  bottom: 80px;
  right: 100px;
}
.house {
  font-size: 4rem;
  color: #1cabe2;
  background: #fff;
  padding:15px;
  border-radius: 50%;
  cursor: pointer;
}
.house:hover {
  background-color: #ececec;
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