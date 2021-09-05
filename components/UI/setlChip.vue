<template>
  <div class="chip">
    <div class="chip__item">
      <img class="chip__icon" :src="url" :alt="name">
      <p class="chip__text">{{name}}</p>
    </div>
      <span v-if="this.type === 'parking'" class="chip__tooltip">Подземная встроенно-пристроенная</span>
  </div>
</template>

<script>
export default {
  name: "setlChip",
  props: {
    type: ''
    // name: '',
    // url: '',
    // tooltip: ''
  },
  computed: {
    name() {
      let name = ''
      this.type ==='flat' ? name = 'Квартира' : name = 'Парковка'
      return name
    },
    url(){
      let url = ''
      this.type ==='flat'? url = '/chip/floorplan.svg' : url = '/chip/car.svg'
      return url
    }
  }
}
</script>

<style lang="sass" scoped>
.chip
  position: relative
  height: 26px
  width: fit-content
  background: #FFFFFF
  box-shadow: 0 0 2px rgba(94, 119, 157, 0.25)
  border-radius: 32px
  padding: 0 16px
  display: flex
  align-items: center
  cursor: url('/finger.svg'), default
  &__item
    display: flex
    align-items: center
  &__icon
    width: 14px
    height: 14px
    margin-right: 8px
  &__text
    margin: 0
    font:
      size: 12px
    line-height: 16px
  &__tooltip
    visibility: hidden
    display: flex
    align-items: center
    justify-content: center
    width: fit-content
    height: 44px
    background: #2D2D2D
    opacity: 0.7
    color: #fff
    padding: 0 18px
    position: absolute
    font-size: 13px
    line-height: 20px
    z-index: 1
    white-space: nowrap
    top: 37.5px
    left: 94%
    margin-left: -60px
    &::after
      content: " "
      position: absolute
      bottom: 100%
      left: 4%
      border-width: 7px
      border-style: solid
      border-color: transparent transparent #2D2D2D transparent
      height: 7px
  &:hover .chip__tooltip
    visibility: visible
</style>
