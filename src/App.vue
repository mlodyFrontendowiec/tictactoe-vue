<template>
  <h1 class="h1">Tic Tac Toe</h1>
  <Board />
</template>

<script>
import Board from "./components/Board.vue";

export default {
  name: "App",
  components: { Board },
};
</script>

<style>
.h1 {
  font-family: sans-serif;
  text-align: center;
}
</style>
