<template>
     <div>
         <header class="vff-header">
      <div class="f-container">
        <h1 style="color:white">Quiz Talenti4Future</h1>
      </div>
    </header>
         <flow-form 
            ref="flowform"
            v-bind:questions="questions"
            v-bind:language="language"
            v-on:complete="onComplete"
            v-on:submit="onQuizSubmit"
            v-on:timer="onTimer"
            v-bind:timer="true"
            timer-start-step="html_1" >
        <template v-slot:complete>
        <p>
          <span class="fh2">Wooho! Ce l'hai fatta!</span>
          <span v-if="!submitted" class="f-section-text">
            Rivedi le tue risposte o premi Calcola punteggio per vedere il risultato
          </span>
        </p>
      </template>

      <!-- We've overriden the default "completeButton" slot content -->
      <template v-slot:completeButton>
        <div class="f-submit" v-if="!submitted">
          <button
            class="o-btn-action"
            ref="button"
            type="submit"
            href="#"
            v-on:click.prevent="onQuizSubmit()"
            aria-label="Press to submit">
            <span>Calcola Punteggio</span>
          </button>
          <a 
            class="f-enter-desc"
            href="#"
            v-on:click.prevent="onQuizSubmit()"
            v-html="language.formatString(language.pressEnter)">
          </a>
        </div>
        <p class="text-success" v-if="submitted && time">Tempo trascorso: {{ formattedTime }} </p>
        <p class="text-success" v-if="submitted && score < 4">"il tuo punteggio è di {{ score }} su {{ total }}. Devi aggiornarti di più sul digital marketing!"</p>
        <p class="text-success" v-else-if="submitted && score < 7">"il tuo punteggio è di {{ score }} su {{ total }}. Niente male!"</p>
        <p class="text-success" v-else-if="submitted && score <= total">"il tuo punteggio è di {{ score }} su {{ total }}. Wow, impressionante!"</p>
        <p class="text-success" v-if="submitted && time">
            <g-link to="/">
                <button class="o-btn-action">
                    <span>Torna alla Home</span>
                </button>    
            </g-link>
        </p>
      </template>
     </flow-form>
     </div>
</template>
<script>
import FlowForm, { QuestionModel, QuestionType, ChoiceOption, LanguageModel } from '@ditdot-dev/vue-flow-form'
export default {
    name:"Quiz",
    metaInfo: {
    title: 'Quiz'
  },
    components: {
      FlowForm
    },
        data() {
      return {
        submitted: false,
        completed: false,
        score: 0, 
        total: 8, 
        time: 0,
        formattedTime: '',
        answers: {
          html_1: '3', 
          html_2: '3', 
          html_3: '1', 
          html_4: '2',  
          ux_1: '2', 
          ux_2: '4', 
          ux_3: '4', 
          ux_4: '3', 
        },
        loading:false,
        language: new LanguageModel({
            continue: 'Continua',
            pressEnter: 'oppure premi invio',
            otherPrompt: 'Andere',
            submitText: 'invia questionario',
            skip:'salta',
            completed:"completato"
        }),
        questions: [
          new QuestionModel({
            id: 'start',
            tagline: '8 domande',
            title: 'Quanto ne sai del digital marketing?',
            content: 'Metti alla prova la tua digital marketing knowledge',
            type: QuestionType.SectionBreak,
            required: true,
          }),
          new QuestionModel({
            id: 'html_1',
            title: 'Quale è la più importante delle seguenti funzionalità di un sito web?',
            helpTextShow: false,
            type: QuestionType.MultipleChoice,
            required: true,
            multiple: false,
            options: [
              new ChoiceOption({
                label: 'Mettere a disposizione degli utenti rapporti, analisi e download gratuiti', 
                value: '1'
              }),
              new ChoiceOption({
                label: 'Descrivere i servizi che la vostra azienda fornisce', 
                value: '2'
               }),
              new ChoiceOption({
                label: 'Raccogliere gli indirizzi email dei visitatori', 
                value: '3'
              }), 
              new ChoiceOption({
                label: 'Pubblicare le informazioni di contatto su ogni pagina', 
                value: '4'
              })
            ]
          }),
          new QuestionModel({
            id: 'html_2',
            title: 'Il modo migliore per promuovere un business con i social media è…',
            helpTextShow: false,
            type: QuestionType.MultipleChoice,
            required: true,
            multiple: false,
             options: [
              new ChoiceOption({
                label: 'fare pubblicità dell’azienda, dei servizi e dei prodotti', 
                value: '1'
              }),
              new ChoiceOption({
                label: 'raccogliere quanti più contatti possibili', 
                value: '2'
              }),
              new ChoiceOption({
                label: 'offrire informazioni utili e gratuite', 
                value: '3'
              }),
              new ChoiceOption({
                label: 'invitare i potenziali clienti a visitare il tuo sito web', 
                value: '4'
              })
            ]
          }),
          new QuestionModel({
            id: 'html_3',
            title: 'Parlare di “ottimizzazione sui motori di ricerca on page” si riferisce a…',
            helpText: "Quale suona bene? C'è solo una risposta giusta.",
            type: QuestionType.MultipleChoice,
            required: true,
            multiple: false, 
            options: [
              new ChoiceOption({
                label: 'Definire le parole chiave in un sito web', 
                value: '1'
              }),
              new ChoiceOption({
                label: 'Valutare il design di ogni pagina del sito', 
                value: '2'
              }),
              new ChoiceOption({
                label: 'La quantità di link in entrata nel tuo sito web', 
                value: '3'
              }), 
              new ChoiceOption({
                label: 'Il numero di motori di ricerca in cui il tuo sito è indicizzato', 
                value: '4'
              })
            ] 
          }),
          new QuestionModel({
            id: 'html_4',
            title: 'Il modo migliore per aumentare il ranking sui motori di ricerca è con…',
            type: QuestionType.MultipleChoice,
            multiple: false,
            helpTextShow: false,
            required: true,
            options: [
              new ChoiceOption({
                label: 'I video',
                value: '1'
              }),
              new ChoiceOption({
                label: 'Il blog',
                value: '2'
              }),
              new ChoiceOption({
                label: 'Avere almeno 500 parole di testo per pagina',
                value: '3' 
              }),
              new ChoiceOption({
                label: 'Utilizzando molte immagini per pagina', 
                value: '4'
              })
            ]
          }),
          new QuestionModel({
            title: 'Eccellente! Sei a metà strada🥳',
            content: 'non mollare mancano altre 4 domande!',
            type: QuestionType.SectionBreak
          }),
          new QuestionModel({
            id: 'ux_1',
            title: 'L\'obiettivo principale del “branding” è:',
            type: QuestionType.MultipleChoice,
            multiple: false,
            helpTextShow: false,
            required: true,
            options: [
              new ChoiceOption({
                label: 'Avere potenziali clienti che riconoscono il tuo logo e i tuoi messaggi di vendita', 
                value: '1'
              }),
              new ChoiceOption({
                label: 'Guadagnare la fiducia dei tuoi clienti', 
                value: '2'
              }),
              new ChoiceOption({
                label: 'Avere materiali promozionali che incontrino le esigenze del target e lo guidino', 
                value: '3'
              }),
              new ChoiceOption({
                label: 'Diffondere un unico slogan', 
                value: '4'
              })
            ]
          }),
          new QuestionModel({
            id: 'ux_2',
            title: 'Quale delle seguenti tecniche di marketing paga di più?',
            helpTextShow: false,
            type: QuestionType.MultipleChoice,
            multiple: false,
            required: true,
            options: [
              new ChoiceOption({
                label: 'Pay per click advertising', 
                value: '1'
              }),
              new ChoiceOption({
                label: 'Le strategie di social media marketing', 
                value: '2'
              }),
              new ChoiceOption({
                label: 'Pubblicazione di comunicati stampa', 
                value: '3'
              }),
              new ChoiceOption({
                label: 'Content marketing', 
                value: '4'
              })
            ]
          }),
          new QuestionModel({
            id: 'ux_3',
            title: 'Quando è il momento ideale per inviare un comunicato stampa?',
            type: QuestionType.MultipleChoice,
            multiple: false,
            helpTextShow: false,
            required: true,
            options: [
              new ChoiceOption({
                label: 'Solo quando accade una grossa novità', 
                value: '1'
              }),
              new ChoiceOption({
                label: 'Solo in prossimità delle festività e vacanze', 
                value: '2'
              }),
              new ChoiceOption({
                label: 'Quando la notizia è lenta a diffondersi', 
                value: '3'
              }),
              new ChoiceOption({
                label: 'Su qualunque cosa faccia notizia', 
                value: '4'
              })
            ]
          }),
          new QuestionModel({
            id: 'ux_4',
            title: 'Qual è il modo migliore di fare soldi mentre si dorme?',
            helpTextShow: false,
            type: QuestionType.MultipleChoice,
            multiple: false,
            required: true,
            options: [
              new ChoiceOption({
                label: 'Sognando buone idee di marketing', 
                value: '1'
              }),
              new ChoiceOption({
                label: 'Mettendo i tuoi prodotti in vendita su ebay', 
                value: '2'
              }),
              new ChoiceOption({
                label: 'Mettendo i prodotti sul tuo sito', 
                value: '3'
              }),
              new ChoiceOption({
                label: 'Avere il partner che lavora di notte', 
                value: '4'
              })
            ]
          })
        ]
      }
    },
    metaInfo: {
    title: 'Quiz'
  },
  methods:{
       onComplete(completed, questionList) {
        // This method is called whenever the "completed" status is changed.
        this.completed = completed
      },
      arrayEquals(a, b) {
        return Array.isArray(a) && Array.isArray(b) && a.length === b.length &&
          a.every((val, index) => val === b[index])
      },
      calculateScore() {
        this.questions.forEach(question => {
          if (question.type !== QuestionType.SectionBreak) {
            let answer = question.answer
            if (typeof answer === 'object') {
              answer.sort((a, b) => a - b)
              if (this.arrayEquals(answer, this.answers[question.id])) {
                this.score++
              }
            }
            if (answer == this.answers[question.id]) {
              this.score++
            }
          }
        })
      }, 
      onQuizSubmit() {
        // Set `submitted` to true so the form knows not to allow back/forward
        // navigation anymore.
        this.$refs.flowform.submitted = true
        
        this.submitted = true
        this.calculateScore()
      },
      onTimer(time, formattedTime) {
        this.time = formattedTime
        this.formattedTime = formattedTime
      }
  }
}
</script>
<style scoped>
 /* Import Vue Flow Form base CSS */
  @import '~@ditdot-dev/vue-flow-form/dist/vue-flow-form.css';
  /* Import one of the Vue Flow Form CSS themes (optional) */
  @import '~@ditdot-dev/vue-flow-form/dist/vue-flow-form.theme-minimal.css';
  /* @import '~@ditdot-dev/vue-flow-form/dist/vue-flow-form.theme-green.css'; */
  /* @import '~@ditdot-dev/vue-flow-form/dist/vue-flow-form.theme-purple.css'; */
</style>