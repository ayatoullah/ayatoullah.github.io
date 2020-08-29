<template>
  <section>
    <div class="new-quote">
      <p>Quote</p>
      <textarea id="quote" v-model="newQuote"></textarea>
      <div class="row">
        <div class="col-md-12 text-center">
          <button class="btn btn-default text-center" @click="addQuote()">Add Quote</button>
        </div>
      </div>
    </div>
    <div class="added-quotes">
      <div class="row">
        <div class="col-md-3" v-for="(quote,index) in quotes" v-bind:key="index">
          <div class="added-quote" @click="deleteQuote(index)">{{quote}}</div>
        </div>
      </div>
    </div>
  </section>
</template>
<script>
export default {
  props: ["newQuote", "newWidth"],
  data: function () {
    return {
      quotes: [],
    };
  },
  methods: {
    addQuote: function () {
      if (this.quotes.length < 10) {
        this.quotes.unshift(this.newQuote);
        this.newWidth += 10;
        this.$emit("quoteIsAdded", this.newQuote);
      } else {
        confirm("Please delete some quotes to add another quote");
      }
    },
    deleteQuote: function (index) {
      this.newWidth -= 10;
      this.quotes.splice(index, 1);
      this.$emit("quoteIsRemoved", this.newWidth);
    },
  },
};
</script>
<style scoped>
@import url("https://fonts.googleapis.com/css?family=Tangerine");
.new-quote {
  width: 50%;
  margin: auto;
  /* font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif; */
}
.new-quote textarea {
  font-family: "Tangerine", serif;
  height: 75px;
  border-radius: 1%;
  margin: auto;
  width: 100%;
  border: 1px #ccc solid;
  font-family: dancing;
}
button {
  margin: 5% auto;
}
section {
  margin: 1% 0%;
}
.added-quote {
  border: 1px solid #ccc;
  border-radius: 3px;
  padding: 1%;
  margin: 1%;
  text-align: center;
}
.added-quote:hover {
  background-color: #edc2c0;
  border: 1px solid red;
}
</style>