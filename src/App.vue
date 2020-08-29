<template>
  <div class="container">
    <div>
      <h3>Quotes Added</h3>
    </div>
    <div class="quotes-number">
      <div :style="divStyles">{{width/10}} /10</div>
    </div>
    <new-quote
      :newQuote="quote"
      @quoteIsAdded="addedQuote($event)"
      :newWidth="width"
      @quoteIsRemoved="removedQuote($event)"
    ></new-quote>
    <div class="row">
      <div class="col-md-12 text-center info">info: click on quote to delete it</div>
    </div>
  </div>
</template>

<script>
import NewQuote from "./components/NewQuote.vue";
export default {
  data: function () {
    return {
      quote: "addQuote",
      width: 0,
    };
  },
  methods: {
    addedQuote: function ($event) {
      this.width += 10;
      quote = $event;
    },
    removedQuote: function ($event) {
      this.width = $event;
    },
  },
  components: {
    "new-quote": NewQuote,
  },
  computed: {
    divStyles() {
      return {
        width: `${this.width}%`,
        backgroundColor: "#3278b5",
        borderRadius: "3px",
        color: "white",
        textAlign: "center",
      };
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Tangerine|Inconsolata|Droid+Sans");

.quotes-number {
  background-color: #3278b5;
  height: 20px;
  border-radius: 5px;
  margin: 3%;
  background-color: #eee;
  margin: auto;
  transition: width 500ms;
}

.info {
  background-color: #d5ebf3;
  padding: 1% 0%;
  margin: 1% 0%;
  border-radius: 5px;
  color: #3278b5;
}
</style>
