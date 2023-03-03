<template>
  <form class="search-form">
    <input type="text" :placeholder="placeholder" class="search-form__field" required />
    <input type="submit" value=" " class="search-form__button" />
  </form>
</template>

<script>
export default {
  name: "SearchField",
  props: {
    placeholder: String,
  },
};
</script>

<style lang="scss">
.search-form {
  position: relative;
  display: block;

  &__field {
    width: 402px;
    height: 45px;
    padding-left: 45px;
    background: #f9fafb;
    border: 1px solid #e5e7eb;
    border-radius: 16px;

    &::placeholder {
      color: #6b7280;
    }

    &:-ms-input-placeholder {
      color: #6b7280;
    }

    &::-ms-input-placeholder {
      color: #6b7280;
    }
  }

  &__button {
    position: absolute;
    top: 50%;
    left: 17px;
    width: 20px;
    height: 21px;
    margin-top: -10.5px;
    background: url("~@/assets/img/search.svg") no-repeat;
  }
}
</style>
