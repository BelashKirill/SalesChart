<template>
  <div class="latest-block">
    <div class="title-block">Latest Customers</div>
    <div class="latest-block__items">
      <div class="latest-block__item" v-for="(item, i) in latestCust" :key="i">
        <div class="latest-block__item_left">
          <div class="latest-block__wrap-info">
            <div class="latest-block__img">
              <img src="@/assets/img/Avatar.png" alt="" />
            </div>
            <div class="latest-block__text">
              <div class="latest-block__name">{{ item.name }}</div>
              <div class="latest-block__email">{{ item.email }}</div>
            </div>
          </div>
        </div>
        <div class="latest-block__item_right">
          <div class="latest-block__price">${{ item.price }}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "LatestCustomerBlock",
  data() {
    return {
      latestCust: [
        {
          name: "Neil Sims",
          email: "email@example.com",
          price: 367,
        },
        {
          name: "Neil Sims",
          email: "email@example.com",
          price: 367,
        },
        {
          name: "Neil Sims",
          email: "email@example.com",
          price: 367,
        },
        {
          name: "Neil Sims",
          email: "email@example.com",
          price: 367,
        },
        {
          name: "Neil Sims",
          email: "email@example.com",
          price: 367,
        },
        {
          name: "Neil Sims",
          email: "email@example.com",
          price: 367,
        },
      ],
    };
  },
};
</script>

<style lang="scss">
.latest-block {
  min-width: 380px;
  height: 448px;
  padding: 31px 25px;
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

  &__text {
    margin-left: 9px;
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
  }
}
</style>
