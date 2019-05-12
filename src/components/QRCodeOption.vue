<template>
  <div>
    <fieldset>
      <legend>Text</legend>
      <textarea v-model="text" id="textarea"></textarea>
    </fieldset>
    <fieldset>
      <legend>Error correction level</legend>
      <p>
        <input type="radio" value="L" id="low" v-model="errorCorrectionLevel">
        <label for="low">Low(~7%)</label>
      </p>
      <p>
        <input type="radio" value="M" id="medium" v-model="errorCorrectionLevel">
        <label for="medium">Medium(~15%)</label>
      </p>
      <p>
        <input type="radio" value="Q" id="quartile" v-model="errorCorrectionLevel">
        <label for="quartile">Quartile(~25%)</label>
      </p>
      <p>
        <input type="radio" value="H" id="high" v-model="errorCorrectionLevel">
        <label for="high">High( ~30%)</label>
      </p>
    </fieldset>
    <fieldset>
      <legend>Size</legend>
      <p>
        <input type="radio" value="50" id="size50px" v-model="size">
        <label for="size50px">50px</label>
      </p>
      <p>
        <input type="radio" value="100" id="size100px" v-model="size">
        <label for="size100px">100px</label>
      </p>
      <p>
        <input type="radio" value="200" id="size200px" v-model="size">
        <label for="size200px">200px</label>
      </p>
      <p>
        <input type="radio" value="300" id="size300px" v-model="size">
        <label for="size300px">300px</label>
      </p>
    </fieldset>
    <p>
      <button v-on:click="generate" id="generate">QRコード作成</button>
    </p>
  </div>
</template>
  
<script>
import QRCode from "qrcode";

export default {
  name: "QRCodeOption",
  props: {
    canvas: {
      type: String,
      required: true
    }
  },
  data() {
    return {
      text: "",
      errorCorrectionLevel: "M",
      size: "100"
    };
  },
  methods: {
    generate() {
      let text = this.text;
      QRCode.toCanvas(
        document.getElementById(this.canvas),
        this.text,
        {
          errorCorrectionLevel: this.errorCorrectionLevel,
          width: this.size
        },
        function(error) {
          if (error) {
            alert(error);
          }
        }
      );
    }
  }
};
</script>

<style scoped>
#textarea {
  width: 100%;
}
#generate {
  width: 100%;
}
</style>
