<template>
  <div id="app">
    <div @click="generateRandomFilename()" class="np-button">
      <div>Generate filename</div>
    </div>
    <div v-if="generatedRandomFilename" class="np-filename-container">
      <div class="np-generate-title">Generated filename</div>
      <div>
        {{ generatedRandomFilename }}
      </div>
    </div>
    <div class="np-credits">www.nightprogrammer.com</div>
  </div>
</template>
<script>
import moment from "moment";

export default {
  name: "App",
  data() {
    return {
      generatedRandomFilename: null,
    };
  },
  methods: {
    generateRandomFilename() {
      const randomString = this.generateRandomString(6);
      const currentTimestamp = moment(new Date()).format(
        "MM_DD_YYYY_h_mm_ss_SSS"
      );
      const randomNumber = Math.floor(Math.random() * 1000000);
      const fileExtension = "";
      this.generatedRandomFilename =
        randomString +
        "_" +
        currentTimestamp +
        "_" +
        randomNumber +
        fileExtension;
    },
    generateRandomString(stringLength) {
      let result = "";
      const alphaNumericCharacters =
        "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789";
      const alphabetsLength = alphaNumericCharacters.length;
      for (let i = 0; i < stringLength; i++) {
        result += alphaNumericCharacters.charAt(
          Math.floor(Math.random() * alphabetsLength)
        );
      }
      return result;
    },
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  padding: 12px;
}
.np-button {
  cursor: pointer;
  background: #0059ff;
  width: 160px;
  text-align: center;
  margin: 6px 0 20px 0;
  color: #ffffff;
  padding: 4px;
  border-radius: 4px;
}
.np-credits {
  font-size: 12px;
  margin-top: 12px;
}
.np-generate-title {
  font-weight: 600;
  margin-bottom: 10px;
}
.np-filename-container {
  border: 1px solid #0059ff;
  border-radius: 4px;
  padding: 16px;
  max-width: 380px;
}
</style>
