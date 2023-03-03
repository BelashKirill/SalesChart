<template>
  <div class="top-bar">
    <div class="top-bar__left">
      <div class="top-bar__logo">
        <TheLogo />
        <span class="open-menu" @click="$emit('openMenu')"></span>
      </div>
      <div class="top-bar__s-field">
        <SearchField :placeholder="'Search'" />
      </div>
    </div>
    <div class="top-bar__right">
      <TopBarNoteIcon />
      <div class="top-bar__ava">
        <TopBarUserAvatar />
      </div>
    </div>
  </div>
</template>

<script>
import TheLogo from "@/components/TheLogo.vue";
import SearchField from "@/components/SearchField.vue";
import TopBarUserAvatar from "@/components/TopBarUserAvatar.vue";
import TopBarNoteIcon from "@/components/TopBarNoteIcon.vue";

export default {
  name: "TopBar",
  emits: ["openMenu"],
  components: {
    TheLogo,
    SearchField,
    TopBarUserAvatar,
    TopBarNoteIcon,
  },
};
</script>

<style lang="scss">
.top-bar {
  position: fixed;
  top: 0;
  left: 0;
  z-index: 1;
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 100%;
  height: 70px;
  padding: 0 20px;
  background: #fff;
  border-bottom: 1px solid #e5e7eb;

  &__left,
  &__right {
    display: flex;
    align-items: center;
  }

  &__s-field {
    margin-left: 32px;
  }

  &__ava {
    margin-left: 13px;
  }

  &__logo {
    display: flex;
    align-items: center;
  }
}
</style>
