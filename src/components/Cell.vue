<template>
  <div>
    {{ letter }}
  </div>
</template>

<script>
export default {
  name: "Board",
  data: () => ({}),
  props: {
    letter: {
      type: String,
    },
  },
};
</script>
<style scoped></style>
