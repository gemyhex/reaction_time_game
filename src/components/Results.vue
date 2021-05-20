<template>
  <p>Reaction time : {{ score }}ms</p>
  <h4>{{ scoreMessage }}</h4>
</template>

<script>
export default {
  data() {
    return {
      scoreMessage: "",
    };
  },
  props: ["score"],
  mounted() {
    if (this.score < 250) {
      this.scoreMessage = "Very Fast";
    } else if (this.score > 250 && this.score < 400) {
      this.scoreMessage = "Not Bad";
    } else {
      this.scoreMessage = "Idiot Gamer .. Try again";
    }
  },
};
</script>

<style></style>
