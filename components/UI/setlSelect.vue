<template>
  <v-menu v-model="menu" rounded="0" offset-y nudge-bottom="6" :close-on-content-click="false">
    <template v-slot:activator="{on, attrs}">
      <div class="select" v-bind="attrs" v-on="on">
        <p class="select__text">Все статусы</p>
        <img class="select__img" :class="{ 'select__img_rotated': isRotated }" src="/input/ic_up.svg" alt="стрелка">
      </div>
    </template>
    <div class="select__menu menu">
      <div class="menu__item" v-for="item in list">
        <input class="checkbox checkbox_menu" type="checkbox" :id="item.id" v-model="item.model">
        <label class="checkbox__label-menu" :for='item.id'>{{item.name}}</label>
      </div>
    </div>
  </v-menu>
</template>
<script>
export default {
  name: "setlSelect",
  data() {
    return {
      menu: false,
      isRotated: true,
      list: [
        {name: 'Забронировано', model: true, id: 'booked'},
        {name: 'Продано', model: true, id: 'sold'},
        {name: 'Активно', model: true, id: 'active'}
      ]
    }
  },
  watch: {
    menu() {
      this.menu ? this.isRotated = false : this.isRotated = true
    },
    isBooked() {
      this.$emit('booked')
    },
    isSold() {
      this.$emit('sold')
    },
    isActive() {
      this.$emit('active')
    }
  },
  computed: {
    isBooked() {
      return this.list[0].model
    },
    isSold() {
      return this.list[1].model
    },
    isActive() {
      return this.list[2].model
    }
  }
}
</script>

<style lang="sass" scoped>
.select
  border: 1px solid #C4C4C4
  display: flex
  align-items: center
  justify-content: space-between
  padding-left: 15px
  padding-right: 10px
  width: 190px
  cursor: pointer
  &__text
    line-height: 18px
    font-size: 14px
    margin-bottom: 0
  &__img
    width: 16px
    height: 15px
    &_rotated
      transform: rotate(180deg)
  &__menu
    display: flex
    flex-direction: column
    justify-content: space-between
    width: 190px
    height: 124px
    background-color: white
    padding: 21px 0 21px 20px
.menu__item
  display: flex
  align-items: center
  flex-wrap: nowrap
  height: 19px
.checkbox__label-menu
  margin-left: 15px
  color: #02101C
  font-size: 14px
  line-height: 18px
</style>
