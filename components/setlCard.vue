<template>
  <v-expand-transition>
  <div class="card">
    <div class="card__checkbox">
      <input class="checkbox" type="checkbox" v-model="check">
    </div>
    <div class="card__main">
      <div class="card__left">
        <div class="card__header">
          <div class="card__title">
            <h3 class="card__price">{{listItem.price}} руб.</h3>
            <setl-chip :type="listItem.propertyType"/>
          </div>
          <p class="card__property-name">{{listItem.propertyName}},<span class="card__property-name card__property-name_add">
            {{listItem.propertyAdd}}
          </span>
          </p>
        <div class="card__details details">
          <div class="details__left">
            <p class="details__item">{{listItem.propertyNumber}}</p>
            <p class="details__item" v-if="listItem.roomNumber">{{listItem.roomNumber}}</p>
          </div>
          <div class="details__right">
            <p class="details__item">{{listItem.propertySquare}} м²</p>
            <p class="details__item" v-if="listItem.propertyFloor">{{listItem.propertyFloor}} этаж</p>
          </div>
        </div>
        </div>
        <div class="card__address address">
         <img class="address__logo" src="/address.svg" alt="адрес">
          <p class="address__text" v-html="listItem.address">
          </p>
        </div>
      </div>
      <div class="card__right">
        <setl-status :type="listItem.status"></setl-status>
        <img class="card__pic" :src="listItem.plan" alt="план">
        <p class="card__date">Добавлено {{listItem.date}}</p>
      </div>
    </div>
  </div>
    </v-expand-transition>
</template>

<script>
import SetlStatus from "./UI/setlStatus";
import SetlChip from "./UI/setlChip";
export default {

  name: "setlCard",
  components: {SetlChip, SetlStatus},
  props: {
    listItem: {},
    check: ''
  }
}
</script>

<style lang="sass" scoped>
.card
  display: flex
  width: 489px
  height: 238px
  background-color: white
  color: black
  font-size: 14px
  line-height: 150%
  border: 1px solid #E5E5E5
  &__checkbox
    display: flex
    align-items: center
    justify-content: center
    width: 66px
    height: inherit
  &__main
    width: 100%
    display: flex
    justify-content: space-between
  &__left
    width: fit-content
    display: flex
    flex-direction: column
    justify-content: space-between
  &__title
    padding-top: 22px
    display: flex
  &__price
    margin-top: 3px
    margin-right: 16px
    font:
      weight: 700
      size: 15px
    line-height: 20px
    color: #FF0D29
  &__property-name
    margin-bottom: 0
    margin-top: 3px
    font-weight: inherit
    font-size: inherit
    line-height: 21px
    height: 42px
    width: 225px
    &_add
      color: #9B9B9B
  &__right
    display: flex
    flex-direction: column
    align-items: flex-end
    padding-bottom: 25px
    padding-top: 21px
  &__pic
    margin-right: 25px
    margin-top: 27px
    width: 133px
    height: 103px
  &__date
    margin-top: 12px
    margin-right: 25px
    margin-bottom: 0
    font-size: 13px
    color: #9B9B9B
  .details
    margin-top: 14px
    display: flex
    &__left
      padding-right: 20px
      border-right: 1px solid #C4C4C4
    &__right
      padding-left: 20px
    &__item
      margin-bottom: 0
      width: fit-content
      line-height: 25px
  .address
    padding-bottom: 25px
    margin-left: -19px
    display: flex
    align-items: flex-start
    &__logo
      margin-top: 4px
      margin-right: 6px
      width: 13px
      height: 13px
    &__text
      margin-bottom: 0
      line-height: 21px
      display: flex


</style>
