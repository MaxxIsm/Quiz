<script>
export default {
  props: {
    questions: {
      type: Array,
      required: true,
    },
    questAnswered: {
      type: Number,
      required: true,
    },
  },
  methods: {
    questClicked(is_correct) {
      this.$emit("quest-clicked", is_correct);
    },
  },
};
</script>

<template>
  <div class="questions-ctr">
    <div class="progress">
      <div
        class="bar"
        :style="{ width: `${(questAnswered / questions.length) * 100}%` }"
      ></div>
      <div class="status">
        {{ questAnswered }} out of {{ questions.length }} questions answered
      </div>
    </div>
    <transition-group name="fade">
      <div
        class="single-question"
        v-for="(question, index) in questions"
        v-show="questAnswered === index"
        :key="question.q"
      >
        <div class="question">
          {{ question.q }}
        </div>
        <div class="answers">
          <div
            class="answer"
            v-for="answer in question.answers"
            :key="answer"
            @click.prevent="questClicked(answer.is_correct)"
          >
            {{ answer.text }}
          </div>
        </div>
      </div>
    </transition-group>
  </div>
</template>

<style></style>
