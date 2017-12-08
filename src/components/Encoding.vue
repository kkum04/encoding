<template>
  <div class="hello">
    <div class="ui fluid icon input">
      <input type="text" placeholder="Input text" v-model="input">
    </div>

    <div class="ui fluid icon input disabled">
      <input type="text" placeholder="EUCKR" :value="EUCKR">
    </div>

    <div class="ui fluid icon input disabled">
      <input type="text" placeholder="UTF8" :value="UTF8">
    </div>
  </div>
</template>

<script>
  import iconv from 'iconv-lite'


  console.dir(iconv);
export default {
  name: 'Encoding',
  data () {
    return {
      msg: 'Welcome to Your Vue.js ',
      input: 'kkum'
    }
  },
  methods: {
    hexEncode(buffer) {
      console.dir(buffer);

      var hex, i;

      var result = "";
      for (i = 0; i < buffer.length; i++) {
        hex = buffer[i].toString(16);

        if(hex.length < 2) hex += '0';
        result += ' ' + hex;
      }

      return result
    }
  },
  computed: {
    EUCKR() {
      return this.hexEncode(iconv.encode(this.input, "EUC-KR"));
    },
    UTF8() {
      return this.hexEncode(iconv.encode(this.input, 'UTF-8'));
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
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
