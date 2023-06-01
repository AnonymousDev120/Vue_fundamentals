<template>
  <div>{{ greeting }}</div>
  <div>{{ work }}</div>
  <div v-html="work"></div>
  <h2 v-bind:id="headingID">Heading</h2>
  <button v-bind:disabled="isDisabled">Bind</button>
  <h2 class="underline">Underlined Text</h2>
  <h2 class="underline" v-bind:class="status">Status</h2>
  <h2 v-bind:class="isPromoted && 'promoted'">Promoted</h2>
  <h2 v-bind:class="isSoldOut ? 'sold-out' : 'new'">SoldOut</h2>
  <h2 v-bind:class="[isPromoted && 'promoted', isSoldOut ? 'sold-out' : 'new']">
    Array Conditional Class
  </h2>

  <h2
    v-bind:class="{
      promoted: isPromoted,
      new: !isSoldOut,
      'sold-out': isSoldOut,
    }"
  >
    Object Class binding
  </h2>
  <h2
    v-bind:style="{
      color: highlightColor,
      fontSize: headerSize + 'px',
    }"
  >
    Style Bind
  </h2>
  <h2 v-bind:style="headerStyleObj">Object style bind</h2>
  <h2 v-bind:style="[headerStyleObj, headerStyleObj2]">
    Array style object bind
  </h2>
  <h2 v-if="number === 0" @mouseover="mouseoverMethod()">
    Number {{ number }}
  </h2>
  <h2 v-else-if="number < 0" @mouseover="mouseoverMethod()">
    Number is negative {{ number }}
  </h2>
  <h2 v-else-if="number > 0" @mouseover="mouseoverMethod()">
    Number is positive {{ number }}
  </h2>
  <h2 v-else>Not a Number</h2>
  <h1>{{ doSmth() }}</h1>
  <button @click="add()">Add</button>
  <button @click="substract()">Minus</button>
  <input type="text" v-model="number" />
  <input type="text" v-model="name" />
  <div>{{ greeting }} {{ name }}</div>
  <div>
    {{ addX }}
    {{ addY }}
    <button @click="x++">AddX</button>
    <button @click="y++">AddY</button>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      name: "",
      greeting: "Hi",
      work: "<b>Developer</b>",
      headingID: "heading",
      isDisabled: false,
      status: "danger",
      isPromoted: true,
      isSoldOut: true,
      highlightColor: "orange",
      headerSize: 50,
      headerStyleObj: {
        color: "orange",
        fontSize: "50px",
      },
      headerStyleObj2: {
        "text-decoration": "underline",
      },
      number: 0,
      x: 0,
      y: 0,
      users: ["mgmg", "agag", "mama"],
    };
  },
  methods: {
    doSmth: function () {
      return "hi";
    },
    add: function () {
      this.number++;
    },
    substract: function () {
      this.number--;
    },
    mouseoverMethod: function () {
      this.number = 0;
    },
    change: function () {
      alert("hello");
    },
  },
  computed: {
    addX: function () {
      console.log(this.x);
      return this.x;
    },
    addY: function () {
      console.log(this.y);
      return this.y;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.underline {
  text-decoration: underline;
}

.promoted {
  font-style: italic;
}

.new {
  color: green;
}

.sold-out {
  color: red;
}
</style>
