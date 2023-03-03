<template>
  <div class="left-bar" :class="{'left-bar_open': isOpenMenu}">
    <Menu :numMess="1" />
    <div class="left-bar__options">
      <a href="#" class="filter"></a>
      <a href="#" class="globe"></a>
      <a href="#" class="cog"></a>
    </div>
  </div>
</template>

<script>
import Menu from "@/components/Menu.vue";

export default {
  name: "LeftBar",
  props: {
    open: Boolean
  },
  components: {
    Menu,
  },
  computed: {
    isOpenMenu() {
      return this.open;
    }
  }
};
</script>

<style lang="scss">
.left-bar {
  position: fixed;
  top: 0;
  left: 0;
  width: 250px;
  height: 100vh;
  padding: 87px 0 20px;
  background: #fff;
  border-right: 1px solid #e5e7eb;
  transition: ease-out .4s;

  &_open {
    left: -250px;
  }

  &__options {
    position: absolute;
    bottom: 19px;
    left: 50%;
    margin-left: -80px;
    display: flex;
    width: 160px;

    a {
      margin: 0 13.5px;
    }
  }
}
</style>
