<template>
  <div id="container">
    <v-textarea
      rows="1"
      auto-grow
      label="Todo"
      id="Block"
      v-on="listeners"
      :value="value"
    >
    </v-textarea>
  </div>
</template>

<script>
export default {
  props: {
    value: {
      type: String,
      default: "a",
    },
    mounted() {
      this.resize();
    },
  },
  methods: {
    resize() {
      const { textarea } = this.$refs;
      textarea.style.height = textarea.scrollHeight - 4 + "px";
    },
  },
};
</script>

<style lang="scss" scoped>
@import "../variables.scss";
div#container textarea {
  overflow-y: hidden; /* prevents scroll bar flash */
  padding-top: 1.1em; /* prevents text jump on Enter keypress */
}
textarea {
  width: 100%;
  direction: rtl;
  display: block;
  max-width: 100%;
  line-height: 1.5;
  padding: 15px 15px 30px;
  border-radius: 3px;
  border: 1px solid #F7E98D;
  font: 13px Tahoma, cursive;
  transition: box-shadow 0.5s ease;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  font-smoothing: subpixel-antialiased;
  background: linear-gradient(#F9EFAF, #F7E98D);
  background: -o-linear-gradient(#F9EFAF, #F7E98D);
  background: -ms-linear-gradient(#F9EFAF, #F7E98D);
  background: -moz-linear-gradient(#F9EFAF, #F7E98D);
  background: -webkit-linear-gradient(#F9EFAF, #F7E98D);
}
.input {
  width: 100%;
  padding: 8px 10px;
  border: 1px solid $vue-blue;
}
</style>


<!-- Comment


//send all events to parent
//add change blocktype method
//update styles

The `$listeners` is deprecated. (vue/no-deprecated-dollar-listeners-api)
https://v3.vuejs.org/guide/migration/listeners-removed.html

<p id="Block" contenteditable v-model="value"  class="Block" v-on="listeners">

  // computed: {
  //   listeners() {
  //     console.log("this.value: ", this.value);
  //     return {
  //       // Pass all component listeners directly to input
  //       ...this.$listeners,
  //       // Override input listener to work with v-model
  //       input: (event) => this.$emit("input", event.target.value),
  //     };
  // },
  // },




 -->
