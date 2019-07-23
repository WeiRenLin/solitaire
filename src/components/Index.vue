<template>
  <div>
    <div class="card__Top">
      <div class="card__Top__single"></div>
      <div class="card__Top__single"></div>
      <div class="card__Top__single"></div>
      <div class="card__Top__single"></div>
      <div class="card__Top__single">
        <img :src="club" alt />
      </div>
      <div class="card__Top__single">
        <img :src="heart" alt />
      </div>
      <div class="card__Top__single">
        <img :src="diamond" alt />
      </div>
      <div class="card__Top__single">
        <img :src="club" alt />
      </div>
    </div>
    <div class="card__bottom"></div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String
  },
  data() {
    return {
      club: "",
      heart: "",
      diamond: ""
    };
  },
  mounted() {
    this.club = require("../../public/static/image/club.png");
    this.heart = require("../../public/static/image/heart.png");
    this.diamond = require("../../public/static/image/diamond.png");
  }
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
