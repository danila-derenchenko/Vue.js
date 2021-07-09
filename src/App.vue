<template>
  <div id="app" :class="[$style.wrapper]">
    <button @click="clickButton">Add new costs</button>
    <header id="header">
      <h1>My personal costs</h1>
      <main>
        <AddPayment @addNewPayment="addData" />
        <br />
        <PaymentsDisplay :list="paymentsList" />
      </main>
    </header>
  </div>
</template>

<script>
import PaymentsDisplay from "./components/PaymentsDisplay.vue";
import AddPayment from "./components/AddPayment.vue";
export default {
  name: "App",
  components: {
    PaymentsDisplay,
    AddPayment,
  },
  data: () => ({
    paymentsList: [],
  }),
  methods: {
    clickButton() {
      this.element = document.getElementById("header").style.display;
      if (this.element == "none") {
        this.element = "block";
      } else {
        this.element = "none";
      }
    },
    addData(data) {
      console.log("push to state", data);
      this.paymentsList.push(data);
    },
    /*     fetchData() {
      return [
        {
          date: "28.03.2020",
          category: "Food",
          value: 169,
        },
        {
          date: "20.03.2020",
          category: "Sport",
          value: 400,
        },
        {
          date: "28.03.2020",
          category: "Internet",
          value: 200,
        },
      ];
    }, */
  },
  /* created() {
    this.paymentsList = this.fetchData();
  }, */
};
</script>

<style lang="scss" module>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
/* .wrapper {
  background: #2c3e50;
} */
</style>
