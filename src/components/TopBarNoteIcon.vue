<template>
    <div class="note-icon">
        <span class="note-icon__ind"></span>
    </div>
</template>

<script>
export default {
    name: "TopBarNoteIcon"
}
</script>

<style lang="scss">
.note-icon {
    position: relative;
    width: 32px;
    height: 33px;
    background: url('@/assets/img/Notification_Icon.svg') no-repeat;
    cursor: pointer;

    &__ind {
        position: absolute;
        right: 8px;
        top: 5px;
        width: 8px;
        height: 8px;
        background: #E02424;
        border-radius: 100%;
        border: 1px solid #fff;
    }
}
</style>