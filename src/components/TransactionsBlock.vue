<template>
  <div class="transactions-block">
    <div class="title-block">Transactions</div>
    <div class="subtitle-block">This is a list of latest transactions.</div>
    <div class="transactions-block__table">
        <TableTransactions />
    </div>
  </div>
</template>

<script>
import TableTransactions from "@/components/TableTransactions.vue";

export default {
  name: "TransactionsBlock",
  components: {
    TableTransactions
  }
};
</script>

<style lang="scss">
.transactions-block {
  width: 100%;
  height: 473px;
  padding: 31px 25px;
  margin-top: 16px;
  background: #fff;
  box-shadow: 0px 1px 2px rgba(0, 0, 0, 0.06), 0px 1px 3px rgba(0, 0, 0, 0.1);
  border-radius: 16px;

  &__table {
    margin-top: 16px;
  }
}
</style>
