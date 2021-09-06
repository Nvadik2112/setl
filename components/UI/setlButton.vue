<template>
  <button class="button">
    <div class="button__item">
      <p class="button__text">{{name}}</p>
      <img class="button__logo" :src='url' :alt="name">
    </div>
  </button>
</template>

<script>
export default {
  name: "setlButton",
  props: {
    name: '',
    url: ''
  }
}
</script>

<style lang="sass" scoped>
.button
  height: 38px
  width: fit-content
  background-color: #E5E5E5
  padding: 0px 13px
  color: black
  cursor: pointer
  &__item
    display: flex
    align-items: center
  &__text
    margin: 0
    line-height: 20px
    font:
      weight: 400
      size: 13px
    color: inherit
    white-space: nowrap
  &__logo
    margin-left: 6px
    width: 24px
    height: 24px
</style>
