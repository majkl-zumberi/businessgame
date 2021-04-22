<template>
     <div>
         <header class="vff-header">
      <div class="f-container">
        <h1 style="color:white">Questionario TalentPinkies</h1>
      </div>
    </header>
         <flow-form 
            ref="flowform"
            v-bind:questions="questions"
            v-bind:language="language"
            v-on:complete="onComplete"
            v-on:submit="onQuizSubmit" >
        <template v-slot:complete>
        <p>
          <span class="fh2">Wooho!🎉 Ce l'hai fatta!</span>
          <span v-if="!submitted" class="f-section-text">
            Rivedi le tue risposte o premi invia per confermare il questionario
          </span>
        </p>
      </template>

      <!-- We've overriden the default "completeButton" slot content -->
      <template v-slot:completeButton>
        <p class="text-success" v-if="submitted">
            "grazie per aver dedicato il tuo tempo per il questionario, riceverai un feedback al più presto"
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
            tagline: 'Ciao! Benvenuto al nostro sondaggio😊',
            title: 'Questionario ammissione corsi',
            content: 'ti verranno poste domande per cercare di conoscerci meglio. ',
            type: QuestionType.SectionBreak,
            required: true,
          }),
          new QuestionModel({
            id: 'email',
            title: 'Indirizzo email',
            helpTextShow: true,
            tagline: "sarà il mezzo di comunicazione con cui ti invieremo l\'esito di questo questionario",
            helpText: 'sarà il mezzo di comunicazione con cui ti invieremo l\'esito di questo questionario',
            type: QuestionType.Email,
            required: true,
            placeholder: 'Inserisci la tua e-mail'
          }),
          new QuestionModel({
            id: 'anagrafica',
            title: 'Nome e cognome',
            helpTextShow: false,
            type: QuestionType.Text,
            required: true
          }),
          new QuestionModel({
            id: 'diploma',
            title: 'Diploma',
            helpTextShow: false,
            type: QuestionType.MultipleChoice,
            required: true,
            multiple: false, 
            options: [
              new ChoiceOption({
                label: 'Istituto Tecnico', 
                value: 'Istituto Tecnico'
              }),
              new ChoiceOption({
                label: 'Istituto Professionale', 
                value: 'Istituto Professionale'
              }),
              new ChoiceOption({
                label: 'Liceo', 
                value: 'Liceo'
              }), 
              new ChoiceOption({
                label: 'CFP', 
                value: 'CFP'
              })
            ] 
          }),
          new QuestionModel({
            id: 'diploma_context',
            title: 'In cosa ti sei diplomato?',
            type: QuestionType.Text,
            helpTextShow: false,
            required: true,
          }),
          new QuestionModel({
            id: 'describe_yourself',
            title: 'Descriviti con 3 aggettivi',
            helpTextShow: false,
            type: QuestionType.Text,
            required: false,
          }),
          new QuestionModel({
            title: 'Eccellente!',
            content: 'ora parliamo delle tue competenze',
            type: QuestionType.SectionBreak
          }),
          new QuestionModel({
            id: 'competenze_digitali',
            title: 'Come giudichi le tue competenze digitali?',
            type: QuestionType.MultipleChoice,
            multiple: false,
            helpTextShow: false,
            required: true,
            options: [
              new ChoiceOption({
                label: '1', 
                value: '1'
              }),
              new ChoiceOption({
                label: '2', 
                value: '2'
              }),
              new ChoiceOption({
                label: '3', 
                value: '3'
              }),
              new ChoiceOption({
                label: '4', 
                value: '4'
              }),
              new ChoiceOption({
                label: '5', 
                value: '5'
              }),
              new ChoiceOption({
                label: '6', 
                value: '6'
              }),
              new ChoiceOption({
                label: '7', 
                value: '7'
              }),
              new ChoiceOption({
                label: '8', 
                value: '8'
              }),
              new ChoiceOption({
                label: '9', 
                value: '9'
              }),
              new ChoiceOption({
                label: '10', 
                value: '10'
              })
            ]
          }),
          new QuestionModel({
            id: 'competenze_linguistiche',
            title: 'Come giudichi le tue competenze linguistiche?',
            type: QuestionType.MultipleChoice,
            helpTextShow: false,
            multiple: false,
            required: true,
            options: [
              new ChoiceOption({
                label: '1', 
                value: '1'
              }),
              new ChoiceOption({
                label: '2', 
                value: '2'
              }),
              new ChoiceOption({
                label: '3', 
                value: '3'
              }),
              new ChoiceOption({
                label: '4', 
                value: '4'
              }),
              new ChoiceOption({
                label: '5', 
                value: '5'
              }),
              new ChoiceOption({
                label: '6', 
                value: '6'
              }),
              new ChoiceOption({
                label: '7', 
                value: '7'
              }),
              new ChoiceOption({
                label: '8', 
                value: '8'
              }),
              new ChoiceOption({
                label: '9', 
                value: '9'
              }),
              new ChoiceOption({
                label: '10', 
                value: '10'
              })
            ]
          }),
          new QuestionModel({
            id: 'competenze_marketing',
            title: 'Come giudichi le tue competenze nell\'ambito del marketing?',
            type: QuestionType.MultipleChoice,
            helpTextShow: false,
            multiple: false,
            required: true,
            options: [
              new ChoiceOption({
                label: '1', 
                value: '1'
              }),
              new ChoiceOption({
                label: '2', 
                value: '2'
              }),
              new ChoiceOption({
                label: '3', 
                value: '3'
              }),
              new ChoiceOption({
                label: '4', 
                value: '4'
              }),
              new ChoiceOption({
                label: '5', 
                value: '5'
              }),
              new ChoiceOption({
                label: '6', 
                value: '6'
              }),
              new ChoiceOption({
                label: '7', 
                value: '7'
              }),
              new ChoiceOption({
                label: '8', 
                value: '8'
              }),
              new ChoiceOption({
                label: '9', 
                value: '9'
              }),
              new ChoiceOption({
                label: '10', 
                value: '10'
              })
            ]
          }),
          new QuestionModel({
            id: 'skills',
            title: 'Come reputi le tue skills nel team working?',
            helpTextShow: false,
            type: QuestionType.MultipleChoice,
            multiple: false,
            required: true,
            options: [
              new ChoiceOption({
                label: 'Ottime', 
                value: '1'
              }),
              new ChoiceOption({
                label: 'Buone', 
                value: '2'
              }),
              new ChoiceOption({
                label: 'Così Così', 
                value: '3'
              }),
              new ChoiceOption({
                label: 'Scarse', 
                value: '4'
              })
            ]
          }),
          new QuestionModel({
            id: 'problem_solving',
            title: 'In che modo riesci a trovare la soluzione ad un problema?',
            helpText: 'puoi selezionare più di una voce',
            type: QuestionType.MultipleChoice,
            multiple: true,
            required: true,
            options: [
              new ChoiceOption({
                label: 'Cerco su internet', 
                value: 'Cerco su internet'
              }),
              new ChoiceOption({
                label: 'Chiedo aiuto a conoscenti', 
                value: 'Chiedo aiuto a conoscenti'
              }),
              new ChoiceOption({
                label: 'Mi baso su quello che ho studiato', 
                value: 'Mi baso su quello che ho studiato'
              })
            ]
          }),
          new QuestionModel({
            id: 'attività',
            title: 'Pianifichi con metodicità le varie attività da svolgere?',
            helpTextShow: false,
            type: QuestionType.MultipleChoice,
            multiple: false,
            required: true,
            options: [
              new ChoiceOption({
                label: 'Sì', 
                value: true
              }),
              new ChoiceOption({
                label: 'No', 
                value: false
              })
            ]
          })
        ]
      }
    },
    metaInfo: {
    title: 'Questionario'
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
      onQuizSubmit() {
        // Set `submitted` to true so the form knows not to allow back/forward
        // navigation anymore.
        this.$refs.flowform.submitted = true
        
        this.submitted = true
        console.log({questions:this.questions})
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