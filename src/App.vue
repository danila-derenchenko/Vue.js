<template>
  <div id="app" :class="[$style.wrapper]">
    <button @click="clickButton">Add new costs</button>
    <header>
      <h1>My personal costs</h1>
      <main>
        <AddPayment @addNewPayment="addData" v-show="click" />
        <br />
        <CategorySelect :categories="categories" />
        Total: {{ getFPV }}
        <PaymentsDisplay :list="paymentsList" />
      </main>
    </header>
  </div>
</template>

<script>
import PaymentsDisplay from "./components/PaymentsDisplay.vue";
import AddPayment from "./components/AddPayment.vue";
import CategorySelect from "./components/CategorySelect.vue";
import { mapMutations, mapGetters, mapActions } from "vuex";
export default {
  name: "App",
  components: {
    PaymentsDisplay,
    AddPayment,
    CategorySelect,
  },
  data: () => ({
    click: false,
  }),
  methods: {
    ...mapMutations(["setPaymentListData", "addDataToPaymentsList"]),
    clickButton() {
      if (this.click === true) {
        this.click = false;
      } else {
        this.click = true;
      }
    },
    addData(data) {
      console.log("push to state", data);
      //this.paymentsList.push(data);
      //this.paymentsList = [...this.paymentsList, data];
      this.addDataToPaymentsList(data);
    },
    /* fetchData() {
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
  computed: {
    ...mapGetters({
      paymentsList: "getPaymentList",
      categories: "getCategoryList",
    }),
    ...mapActions(["fetchData", "fetchCategory"]),
    getFPV() {
      return this.$store.getters.getFullPyamentValue;
    },
    /*  paymentsList() {
      return this.$store.getters.getPaymentList;
    }, */
  },
  created() {
    //this.$store.commit("setPaymentListData", this.fetchData()); // mutations
    //this.setPaymentListData(this.fetchData());
    //this.$store.dispatch("fetchData"); // actions
    this.fetchData;
    if (!this.categories.length) {
      this.fetchCategory;
    }
    //this.paymentsList = this.fetchData();
  },
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
