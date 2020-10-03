<template>
  <div class="hello">
    <label for="plz">PLZ</label>
    <input type="text" name="" id="plz" v-model="plz" />
    <label for="qm">QM</label>
    <input type="text" id="qm" @input="calc" v-model="qm" />
    <div>{{ calcu }}</div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "HelloWorld",
  data() {
    return {
      calcu: "Bitte werte einpflegen",
      plz: null,
      qm: null,
    };
  },
  props: {
    msg: String,
  },
  methods: {
    calc() {
      console.log("yeah!");
      axios
        .post("http://localhost:8080/api/calc", {
          plz: this.plz,
          qm: this.qm,
        })
        .then((res) => {
          console.log(res);
          this.calcu = res.data.post.calc;
        });
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
