<template>
  <div class="home">
    <userInput />
  </div>
</template>

<script>
// @ is an alias to /src
import userInput from "@/components/userInput.vue";

export default {
  name: "Home",
  components: {
    userInput
  }
};
</script>
