<template>
  <div :class="`status status_${type}`">
    <div class="status__item">
      <div class="status__dot">
      </div>
      <p class="status__text">{{name}}</p>
    </div>
  </div>
</template>

<script>
export default {
name: "setlStatus",
  props: {
    type: ''
  },
  computed: {
    name() {
      let str = ''
      switch (this.type) {
        case 'booked':
          str = 'Забронировано'
          break;
        case 'sold':
          str = 'Продано'
          break;
        case 'individual':
          str = 'Уступка от физ. лица'
          break;
        case 'legal':
          str = 'Уступка от юр. лица'
          break;
        default:
          str = ''
      }
      return str
    }
  }
}
</script>

<style lang="sass" scoped>

.status
  height: 30px
  width: fit-content
  padding: 0 9px
  display: flex
  align-items: center
  &_booked
    background-color: #EDEDED
    color: #686868
  &_sold
    background-color: #CCCCCC
    color: #808080
  &_individual
    background-color: #D6F5FF
    color: #0291C1
  &_legal
    background-color: #FFE4E4
    color: #DD4C5D
  &__item
    display: flex
    align-items: center
  &__dot
    background-color: currentColor
    color: inherit
    width: 6px
    height: 6px
    border-radius: 3px
    margin-right: 8px
  &__text
    margin: 0
    line-height: 18px
    font-size: 14px
</style>
