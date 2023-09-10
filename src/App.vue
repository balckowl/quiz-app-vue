<script setup>
import AnswerList from './components/AnswerList.vue'
import { ref } from 'vue'

const questions = [
  {
    question: '世界で最も使われているUIフレームワークは次のうちどれですか？',
    answers: ['react', 'vue', 'svelte', 'angular'],
    correct: 'react'
  },
  {
    question: 'このクイズアプリは何のUIフレームワークで構築されているでしょうか？',
    answers: ['react', 'vue', 'svelte', 'angular'],
    correct: 'react'
  }
]

let currentNumber = ref(0)
let questionNumber = ref(Math.floor(Math.random() * questions.length))
let correctNumber = ref(0)
let incorrectNumber = ref(0)

const handleJudge = (e) => {
  if (e.target.textContent == questions[questionNumber.value].correct) {
    correctNumber.value++
    alert('正解')
  } else {
    incorrectNumber.value++
    alert('不正解')
  }
  currentNumber.value++
  questionNumber.value = Math.floor(Math.random() * questions.length)
}
</script>

<template>
  <v-app>
    <v-app-bar>
      <v-app-bar-title>
        クイズアプリ
      </v-app-bar-title>
    </v-app-bar>

    <v-main>
      <v-container>
        <v-row>
          <v-col lg="12">
            <v-card>
              <v-card-text class="pa-15">
                <h1 class="pb-4">問題{{ currentNumber + 1 }}</h1>
                <p class="pb-5">{{ questions[questionNumber].question }}</p>
                <AnswerList v-bind:answers="questions[questionNumber].answers" v-bind:handleJudge="handleJudge" />
              </v-card-text>
            </v-card>
          </v-col>
        </v-row>
        <v-row>
          <v-col cols="2">
            <v-card>
              <v-card-text>
                正解数: {{ correctNumber }}
              </v-card-text>
            </v-card>
          </v-col>
          <v-col cols="2">
            <v-card>
              <v-card-text>
                不正解数: {{ incorrectNumber }}
              </v-card-text>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>