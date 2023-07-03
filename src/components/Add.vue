<template>
  <div>
    <Header />

    <h1>Add Transaction</h1>
    <form class="addtrans">
      <input
        type="text"
        name="accountNumber"
        placeholder="Account Number"
        v-model="transaction.accountNumber"
      />
      <input
        type="text"
        name="transactionId"
        placeholder="Transaction-ID"
        v-model="transaction.transactionId"
      />
      <input
        type="date"
        name="date"
        placeholder=" Date "
        v-model="transaction.date"
      />
      <input
        type="text"
        name="paymentMethod"
        placeholder="Payment Method "
        v-model="transaction.paymentMethod"
      />
      <input
        type="number"
        name="amount"
        placeholder="Amount "
        v-model="transaction.amount"
      />
      <button type="button" v-on:click="addTransaction">
        Add New Transaction
      </button>
    </form>
    <!-- <button type="button" v-on:click="viewTransaction">
        View Transactions
      </button> -->
  </div>
</template>

<script>
import Header from "./Header.vue";
import axios from "axios";

export default {
  name: "Home",
  components: {
    Header,
  },
  data() {
    return {
      transaction: {
        accountNumber: "",
        transactionId: "",
        date: "",
        paymentMethod: "",
        amount: "",
      },
    };
  },
  methods: {
    async addTransaction() {
      console.warn("this.transaction");
      const result = await axios.post("http://localhost:3000/transactions", {
        accountNumber: this.transaction.accountNumber,
        transactionId: this.transaction.transactionId,
        date: this.transaction.date,
        paymentMethod: this.transaction.paymentMethod,
        amount: this.transaction.amount,
      });
    },
  },
  async mounted(){
 let result = await axios.get("http://localhost:3000/transactions");
    console.warn(result);
    // this.saver = result.data;

  }
};
</script>
