<template>
  <div class="wrapper">
    <TopBar @openMenu="openMenuMobile" />
    <LeftBar :open="openMenuM" />
    <div class="wrapper__content">
      <ChartBlock />
      <div class="wrapper__middle">
        <LatestCustomerBlock />
        <TopProductsBlock />
      </div>
      <div class="wrapper__table">
        <TransactionsBlock />
      </div>
      <div class="wrapper__footer">
        <TheFooter />
      </div>
    </div>
  </div>
</template>

<script>
import TopBar from "@/components/TopBar.vue";
import LeftBar from "@/components/LeftBar.vue";
import ChartBlock from "@/components/ChartBlock.vue";
import LatestCustomerBlock from "@/components/LatestCustomerBlock.vue";
import TopProductsBlock from "@/components/TopProductsBlock.vue";
import TransactionsBlock from "@/components/TransactionsBlock.vue";
import TheFooter from "@/components/TheFooter.vue";

export default {
  name: "App",
  components: {
    TopBar,
    LeftBar,
    ChartBlock,
    LatestCustomerBlock,
    TopProductsBlock,
    TransactionsBlock,
    TheFooter,
  },
  data() {
    return {
      openMenuM: false,
    };
  },
  methods: {
    openMenuMobile() {
      !this.openMenuM ? this.openMenuM = true : this.openMenuM = false
    }
  },
  mounted() {
    let widthScreen = document.querySelector("#app").clientWidth;

    if (widthScreen <= 768) {
      this.openMenuM = true
    }
  }
};
</script>

<style>
@import url("@/assets/css/normalize.css");
</style>

<style lang="scss">
@import url("@/assets/css/style.scss");
</style>

<style lang="scss">
.wrapper {
  &__content {
    padding: 86px 17px 17px 266px;
  }

  &__middle {
    display: flex;
    justify-content: space-between;
    margin-top: 16px;
  }
}

@media (max-width: 768px) {
  .wrapper__content {
    padding-left: 16px;
  }
}
</style>
