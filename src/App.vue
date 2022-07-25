<template>
  <div id="app">
    <h2>Fullname - {{ firstName }} {{ lastName }}</h2>
    <h2>Fullname - {{ fullName }}</h2>
    <h2>Total - {{ items.reduce((total, curr) => total + curr.price, 0) }}</h2>
    <h2>Computed total - {{ total }}</h2>
    <h2>Method total - {{ getTotal() }}</h2>
    <button @click="items.push({ id: 4, title: 'Keyboard', price: 50 })">
      Add item
    </button>
    <div>
      <input type="text" v-model="country" />
    </div>
    <template v-for="item in items">
      <h2 :key="item.id" v-if="item.id === 1">
        {{ item.title }} - {{ item.price }}
      </h2>
    </template>
    <h2 v-for="item in expensiveItems" :key="item.id">
      {{ item.title }} - {{ item.price }}
    </h2>
    <button @click="changeFullName">Change name</button>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      firstName: "Bruce",
      lastName: "Wayne",
      items: [
        {
          id: 1,
          title: "TV",
          price: 100,
        },
        {
          id: 2,
          title: "Phone",
          price: 200,
        },
        {
          id: 3,
          title: "Laptop",
          price: 300,
        },
      ],
      country: "",
    };
  },

  methods: {
    getTotal() {
      console.log("getTotal");
      return this.items.reduce((total, curr) => total + curr.price, 0);
    },
    changeFullName() {
      this.fullName = "Clark Kent";
    },
  },

  computed: {
    // fullName() {
    //   return `${this.firstName} ${this.lastName}`;
    // },
    fullName: {
      get() {
        return `${this.firstName} ${this.lastName}`;
      },
      set(value) {
        const name = value.split(" ");
        this.firstName = name[0];
        this.lastName = name[1];
      },
    },
    total() {
      console.log("computed total");
      return this.items.reduce((total, curr) => total + curr.price, 0);
    },
    expensiveItems() {
      return this.items.filter((item) => item.price > 100);
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  margin-top: 60px;
}
</style>
