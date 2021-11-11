<template>
  <div>
    <form @submit="formValue">
      <input type="text" placeholder="Event Name" name="name" v-model="evt" />
      <input type="submit" /> <br />
      <br />
      <canvas
        id="myCanvas"
        width="1000"
        height="500"
        style="border: 1px solid #d3d3d3"
        v-insert-message="evt"
      >
        Browser don't support canvas.</canvas
      >
    </form>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },

  mounted() {},

  data() {
    return {
      evt: "",
    };
  },

  directives: {
    insertMessage: function (canvasElement, binding) {
      var ctx = canvasElement.getContext("2d");
      ctx.clearRect(0, 0, 300, 150);
      ctx.fillStyle = "black";
      ctx.font = "145px Helvetica";
      ctx.fillText(binding.value, 340, 110);

      const drawImage = (src) => {
        var ctx = canvasElement.getContext("2d");
        const image = new Image();
        image.src = src;
        image.onload = () => {
          ctx.drawImage(image, 10, 10, 330, 98.0);
        };
      };
      drawImage(require("../assets/tedx_logo.png"));
    },
  },
};
</script>

<style scoped></style>
