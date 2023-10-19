<template>
  <div class="d-flex align-center flex-column">
    <v-card width="500px" elevation="8">
      <v-card-title>Card Title</v-card-title>
      <v-card-text>
        <p>{{ joke.question }}</p>
        <p>{{ joke.answer }}</p>
      </v-card-text>

      <v-card-actions>
        <v-spacer></v-spacer>
        <v-btn color="primary" @click="getJoke">New Joke</v-btn>
        <v-btn color="primary">cancel</v-btn>
      </v-card-actions>
    </v-card>
  </div>
</template>

<script setup lang="ts">
let joke = ref({ question: "", answer: "" });
async function getJoke() {
  $fetch("https://simplejokeapi.azurewebsites.net/joke").then((data: any) => {
    joke.value = data;
  });
}
await getJoke();
</script>
