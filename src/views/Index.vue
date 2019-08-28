<template>
  <div>
    <div>
      <Question
        v-for="(question, index) in questions"
        :key="index"
        @answerRight="answerRight()"
        @answerWrong="answerWrong()"
        @disable="question.disabled = true"
        :disabled="question.disabled"
        :question="question.question"
        :options="question.options"
      ></Question>
    </div>
    <div>
      <Result
        :answered="answered"
        :score="score"
        :finished="finished"
        @reload="reload()"
      ></Result>
    </div>
  </div>
</template>

<script>
import Question from "@/components/Question.vue";
import Result from "@/components/Result.vue";

export default {
  name: "app",
  components: { Question, Result },

  computed: {
    total() {
      return this.questions.length;
    }
  },

  data() {
    return {
      score: 0,
      answered: 0,
      finished: false,
      questions: [
        {
          disabled: false,
          question: "Qual o objetivo de Tanjirou?",
          options: [
            {
              text: "Se tornar o rei dos piratas.",
              correct: false,
              danger: false,
              success: false
            },
            {
              text: "Virar Hokage da Aldeia da Folha.",
              correct: false,
              danger: false,
              success: false
            },
            {
              text: "Se tornar o melhor herói.",
              correct: false,
              danger: false,
              success: false
            },
            {
              text: "Curar sua irmã.",
              correct: true,
              danger: false,
              success: false
            }
          ]
        },
        {
          disabled: false,
          question: "Por que Thorfinn quer matar Askeladd?",
          options: [
            {
              text: "Porque ele roubou pão na casa do João.",
              correct: false,
              danger: false,
              success: false
            },
            {
              text: "Para vingar a morte de seu pai.",
              correct: true,
              danger: false,
              success: false
            },
            {
              text: "Para se tornar o líder dos vinkings.",
              correct: false,
              danger: false,
              success: false
            },
            {
              text: "Para roubar suas riquezas.",
              correct: false,
              danger: false,
              success: false
            }
          ]
        },
        {
          disabled: false,
          question: "Qual o maior inimigo de Guts?",
          options: [
            {
              text: "O líder do Bando do Falcão, Griffith.",
              correct: true,
              danger: false,
              success: false
            },
            {
              text: "O grande bruxo, Lord Voldemort.",
              correct: false,
              danger: false,
              success: false
            },
            {
              text: "O homúnculo Ira.",
              correct: false,
              danger: false,
              success: false
            },
            {
              text: "O jovem psicopata, Johan.",
              correct: false,
              danger: false,
              success: false
            }
          ]
        }
      ]
    };
  },

  methods: {
    answerRight() {
      this.answered++;
      this.score++;
      if (this.answered == this.total) {
        this.finish();
      }
    },
    answerWrong() {
      this.answered++;
      if (this.answered == this.total) {
        this.finish();
      }
    },
    finish() {
      this.finished = true;
    },
    reload() {
      console.log("reload");
      this.$emit("reRender");
    }
  }
};
</script>
