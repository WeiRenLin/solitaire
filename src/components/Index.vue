<template>
  <div>
    <div class="card__Top">
      <div class="card__Top__single"></div>
      <div class="card__Top__single"></div>
      <div class="card__Top__single"></div>
      <div class="card__Top__single"></div>
      <div class="card__Top__single">
        <img :src="spades" alt />
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
    <div id="un-order-decks" :style="{display:setDisplay,justifyContent:setJustify}"></div>
    <button @click="shuffle">123</button>
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
      diamond: "",
      spades: "",
      flex: "flex",
      justifyContent: "space-around",
      deckArray: [{ id: 1, value: "13" }],
      allPoker: 52
    };
  },
  methods: {
    shuffle: function(array) {
      for (let i = array - 1; i > 0; i--) {
        let j = Math.floor(Math.random() * (i + 1));
        [array[i], array[j]] = [array[j], array[i]];
      }
      return array;
    },
    displayInitialDeck() {
      const porkerArray = Array.from(new Array(52)).map((_, index) => {
        return index + 1;
      });
      const shuffleDeck = this.shuffle(porkerArray);
      shuffleDeck.map((number, _) => {
        // if(ignoreCard.indexOf(number) !== -1)return;
        const randomDeckNum = this.createRandomDeckNum();
        this.deckArray[shuffleDeck].push(number);
      });
    },
    createRandomDeckNum() {
      const randomNum = Math.floor(Math.random() * (7 - 0 + 1)) + 0;
      alert(randomNum);

      if (randomNum <= 3) {
        if (this.deckArray[randomNum].length >= 6) {
          return this.createRandomDeckNum();
        }
      } else {
        if (this.deckArray[randomNum].length >= 5) {
          return this.createRandomDeckNum();
        }
      }
      return randomNum;
    },
    flushDecks: function() {
      ///
      // unOrderDecks.forEach((decks,index)=> {
      //   const unOrderDecksElem = document.createElement("div");
      // unOrderDecksElem.class ='un-order-dock-${index}';
      // unOrderDecksElem.style.position = 'relative';
      // unOrderDecksElem.style.height='600px';
      // unOrderDecksElem.style.width='152px';
      // unOrderDecksElem.style.fontsize='16px';
      // unOrderDecksElem.style.userSelect='none';
      //   decks.forEach((card,cardIndex) => {
      //     // const unOrderDecksCardElem
      //   });
      // });
    },
    transNumberToColor(cardNumber) {
      ///黑桃 (1-13) || 紅心 (14-26) || 磚塊 (27-39) || 梅花 (40-52)
      if (cardNumber > 0 && cardNumber <= 13) return "spade";
      if (cardNumber > 13 && cardNumber <= 26) return "heart";
      if (cardNumber > 27 && cardNumber <= 39) return "diamond";
      if (cardNumber > 40 && cardNumber <= 52) return "club";
    }
  },
  computed: {
    setDisplay: function() {
      return this.flex;
    },
    setJustify: function() {
      return this.justifyContent;
    }
  },
  mounted() {
    this.displayInitialDeck();
    this.shuffle();
    this.club = require("../../public/static/image/club.png");
    this.heart = require("../../public/static/image/heart.png");
    this.diamond = require("../../public/static/image/diamond.png");
    this.spades = require("../../public/static/image/spades.png");
    this.flushDecks();
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
