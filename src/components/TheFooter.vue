<template>
  <div class="footer">
    <div class="footer__copiright">© 2021 Themesberg, LLC. All rights reserved.</div>
    <div class="footer__social-icons">
        <a href="#" target="_blank" class="facebook"></a>
        <a href="#" target="_blank" class="twitter"></a>
        <a href="#" target="_blank" class="github"></a>
        <a href="#" target="_blank" class="dribble"></a>
    </div>
  </div>
</template>

<script>
export default {
  name: "TheFooter",
};
</script>

<style lang="scss">
.footer {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 100%;
  height: 120px;
  padding: 31px 41px;
  margin-top: 16px;
  background: #fff;
  border-radius: 16px;

  &__copiright {
    font-weight: 400;
    font-size: 16px;
    color: #6b7280;
  }

  &__social-icons {
    display: flex;
    align-items: center;

    a {
        margin-left: 23px;
    }
  }
}
</style>
