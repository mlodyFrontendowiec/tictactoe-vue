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
    step: 0,
  }),
  methods: {
    setChar(id) {
      if (this.arrOfLetters[id] !== "") return;
      this.arrOfLetters[id] = this.actualChar;
      setTimeout(() => {
        this.checkWhoWin();
      });
      this.step++;
    },
    changeChar() {
      if (this.actualChar === "O") {
        this.actualChar = "X";
      } else this.actualChar = "O";
    },
    checkWhoWin() {
      if (
        (this.arrOfLetters[0] === this.actualChar &&
          this.arrOfLetters[1] === this.actualChar &&
          this.arrOfLetters[2] === this.actualChar) ||
        (this.arrOfLetters[3] === this.actualChar &&
          this.arrOfLetters[4] === this.actualChar &&
          this.arrOfLetters[5] === this.actualChar) ||
        (this.arrOfLetters[6] === this.actualChar &&
          this.arrOfLetters[7] === this.actualChar &&
          this.arrOfLetters[8] === this.actualChar) ||
        (this.arrOfLetters[0] === this.actualChar &&
          this.arrOfLetters[4] === this.actualChar &&
          this.arrOfLetters[8] === this.actualChar) ||
        (this.arrOfLetters[2] === this.actualChar &&
          this.arrOfLetters[4] === this.actualChar &&
          this.arrOfLetters[6] === this.actualChar) ||
        (this.arrOfLetters[0] === this.actualChar &&
          this.arrOfLetters[3] === this.actualChar &&
          this.arrOfLetters[6] === this.actualChar) ||
        (this.arrOfLetters[1] === this.actualChar &&
          this.arrOfLetters[4] === this.actualChar &&
          this.arrOfLetters[7] === this.actualChar) ||
        (this.arrOfLetters[2] === this.actualChar &&
          this.arrOfLetters[5] === this.actualChar &&
          this.arrOfLetters[8] === this.actualChar)
      ) {
        alert("The winner is " + this.actualChar);
        window.location.reload();
      } else if (this.step === 9) {
        alert("DRAW");
        window.location.reload();
      } else {
        this.changeChar();
      }
    },
  },
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
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
