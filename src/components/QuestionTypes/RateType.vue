<template>
  <b-rate
    ref="input"
    v-bind:value="value"
    v-bind:required="question.required"
    v-on:keydown="onKeyDown"
    v-on:keyup="onChange({ target: { value: $event } })"
    v-on:keyup.enter.prevent="onEnter"
    v-on:keyup.tab.prevent="onEnter"
    v-on:focus="setFocus"
    v-on:blur="unsetFocus"
    v-on:change="onChange({ target: { value: $event } })"
    v-bind:placeholder="placeholder"
  />
</template>

<script>
import BaseType from "./BaseType.vue";
import { QuestionType } from "../../models/QuestionModel";
import "@mdi/font/css/materialdesignicons.css"; // Ensure you are using css-loader
import "buefy/dist/buefy.css";

import buefy from "buefy";
import Vue from "vue";
Vue.use(buefy);
// import { Rate } from "buefy";

export default {
  extends: BaseType,
  name: QuestionType.Rate,
  //   components: { Rate },

  data() {
    return {
      canReceiveFocus: false
    };
  },

  methods: {
    validate() {
      return !this.question.required || this.hasValue;
    }
  }
};
</script>
