<script setup>
defineProps(['answers', 'handleJudge', 'currentNumber']);
</script>

<template>
    <ul class="d-flex answers">
        <template v-for="answer in answers">
            <li v-on:click = "handleJudge"><v-btn>{{ answer }}</v-btn></li>
        </template>
    </ul>
</template>