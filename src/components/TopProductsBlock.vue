<template>
  <div class="products-block">
    <div class="title-block">Top products</div>
    <div class="products-block__items">
      <div class="products-block__item" v-for="(item, i) in topProd" :key="i">
        <div class="products-block__item_left">
          <div class="products-block__wrap-info">
            <div class="products-block__text">
              <div class="products-block__name">{{ item.name }}</div>
              <div class="products-block__email">{{ item.text }}</div>
            </div>
          </div>
        </div>
        <div class="products-block__item_right">
          <div class="products-block__price">{{ item.sales }} <span>sales</span></div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "TopProductsBlock",
  data() {
    return {
      topProd: [
        {
          name: "Restaurant Booking App",
          text: "React & Bootstrap Framework",
          sales: 70,
        },
        {
          name: "Restaurant Booking App",
          text: "React & Bootstrap Framework",
          sales: 70,
        },
        {
          name: "Restaurant Booking App",
          text: "React & Bootstrap Framework",
          sales: 70,
        },
        {
          name: "Restaurant Booking App",
          text: "React & Bootstrap Framework",
          sales: 70,
        },
        {
          name: "Restaurant Booking App",
          text: "React & Bootstrap Framework",
          sales: 70,
        },
        {
          name: "Restaurant Booking App",
          text: "React & Bootstrap Framework",
          sales: 70,
        },
      ],
    };
  },
};
</script>

<style lang="scss">
.products-block {
  width: 100%;
  height: 448px;
  padding: 31px 25px;
  margin-left: 16px;
  background: #fff;
  box-shadow: 0px 1px 2px rgba(0, 0, 0, 0.06), 0px 1px 3px rgba(0, 0, 0, 0.1);
  border-radius: 16px;

  &__items {
    margin-top: 18px;
  }

  &__item {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 9px 0;
    border-bottom: 1px solid #e5e7eb;

    &:first-child {
      border-top: 0;
    }

    &:last-child {
      border-bottom: 0;
    }
  }

  &__wrap-info {
    display: flex;
    align-items: center;
  }

  &__name {
    font-weight: 600;
    font-size: 16px;
  }

  &__email {
    font-size: 12px;
    color: #6b7280;
  }

  &__price {
    font-weight: 600;
    font-size: 16px;

    span {
      color: #4b5563;
    }
  }
}
</style>
