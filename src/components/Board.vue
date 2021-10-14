<template>
  <section class="wrapper">
    <div
      v-for="(letter, id) in arrOfLetters"
      :key="id"
      @click="setChar(id)"
      class="cell"
    >
      {{ letter }}
    </div>
  </section>
</template>

<script>
export default {
  name: "Board",
  data: () => ({
    arrOfLetters: ["", "", "", "", "", "", "", "", ""],
    actualChar: "O",
  }),
  methods: {
    setChar(id) {
      if (this.arrOfLetters[id] !== "") return;
      this.arrOfLetters[id] = this.actualChar;
      this.changeChar();
    },
    changeChar() {
      if (this.actualChar === "O") {
        this.actualChar = "X";
      } else this.actualChar = "O";
    },
  },
  computed: {},
};
</script>
<style scoped>
.wrapper {
  display: flex;
  flex-wrap: wrap;
  width: 190px;
  height: 190px;
  align-items: center;
  justify-content: space-between;
  margin: 100px auto;
}
.cell {
  width: 60px;
  height: 60px;
  background-color: cadetblue;
  font-family: sans-serif;
}
</style>
