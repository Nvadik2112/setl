<template>
  <div class="main">
    <div class="inputs">
      <div class="input-search">
        <img src="/input/search.svg" alt="поиск">
        <input type="text" placeholder="Введите ЖК / корпус / № квартиры / № паркинга">
      </div>
      <setl-select @booked="setIsBooked" @sold="setIsSold" @active="setIsActive" />
      <setl-button name="Очистить корзину" url="/button/x.svg" />
    </div>
    <div class="bar">
      <input class="checkbox checkbox_all" type="checkbox" id="all" v-model="check">
      <label class="checkbox__label-all" for="all">все</label>
      <div class="buttons">
        <setl-button v-for="item in listButton" :name="item.name" :url="item.url" />
      </div>
    </div>
    <div class="cards">
      <setl-card v-for="item in listFilter" :list-item="item" :check="check"/>
    </div>
  </div>
</template>
<script>

import setlButton from "../components/UI/setlButton";
import SetlChip from "../components/UI/setlChip";
import SetlStatus from "../components/UI/setlStatus";
import SetlCard from "../components/setlCard";
import SetlSelect from "../components/UI/setlSelect";
export default {
  name: 'index',
  components: {SetlSelect, SetlCard, SetlStatus, SetlChip, setlButton},
  data() {
    return {
      check: false,
      isBooked: true,
      isSold: true,
      isActive: true,
      listButton: [
        {name: 'Сохранить', url: '/button/pdf.svg'},
        {name: 'Отправить', url: '/button/send.svg'},
        {name: 'Удалить', url: '/button/bin.svg'}
      ],
      listChip: [
        {name: 'Паркинг', url: '/chip/car.svg', tooltip: 'Подземная встроенно-пристроенная'}
      ],
      listStatus: [
        {type: 'sold'}
      ],
      list: [
        {propertyName: 'Чистое Небо', propertyAdd: 'корпус 10, III кв. 2022 г',
          price: '7 733 300', propertyType: 'flat', status: 'legal',
          propertyNumber:'кв. 62', roomNumber: '1 комн. кв', propertyFloor: 7, propertySquare: 234.68 ,
          address: 'Лен. область, Всеволожский район, <br>д. Кудрово, ул. Столичная, д. 5, к. 1',
          plan: '/image.svg', date: '21/11/2020'},

        {propertyName: 'Зеленый квартал на Пулковских высотах', propertyAdd: 'корпус 10, III кв. 2022 г.',
          price: '7 733 300', propertyType: 'flat', status: 'individual',
          propertyNumber:'кв. 62', roomNumber: '1 комн. кв', propertyFloor: 7, propertySquare: 234.68 ,
          address: 'Комендантский пр., уч. 1 Каменка', plan: '/image.svg', date: '21/11/2020'},

        {propertyName: 'Зеленый квартал на Пулковских высотах', propertyAdd: 'корпус 10, III кв. 2022 г',
          price: '800 300', propertyType: 'parking', status: 'booked',
          propertyNumber:'№ 7-10-2 (ПИБ №68)', propertySquare: 15 ,
          address: 'Ленинградская область, Всеволожский<br> район, д. Кудрово, ул. Столичная,<br> д. 5, к. 1',
          plan: '/image.svg', date: '21/11/2020'},

        {propertyName: 'Зеленый квартал на Пулковских высотах', propertyAdd: 'корпус 10, III кв. 2022 г',
          price: '800 300', propertyType: 'parking', status: 'sold',
          propertyNumber:'№ 7-10-2 (ПИБ №68)', propertySquare: 15 ,
          address: 'Лен. область, Всеволожский район, <br>д. Кудрово, ул. Столичная, д. 5, к. 1',
          plan: '/image.svg', date: '21/11/2020'}
      ]
    }
  },
  computed: {
    listFilter() {
      const arr = this.list.filter(elem => (elem.status === 'sold' && this.isSold)
      || (elem.status === 'booked' && this.isBooked) ||
        ((elem.status === 'individual' || elem.status === 'legal') && this.isActive))
      return arr
    }
  },
  methods: {
    setIsBooked() {
      this.isBooked = !this.isBooked
    },
    setIsSold() {
      this.isSold = !this.isSold
    },
    setIsActive() {
      this.isActive = !this.isActive
    }
  }
}
</script>
<style lang="sass" scoped>
.inputs
  width: 1002px
  grid-template-columns: repeat(3, 1fr)
  grid-column-gap: 10px
  display: grid
.input-search
  width: 637px
  border: 1px solid #C4C4C4
  height: 38px
  position: relative
  & img
    position: absolute
    top: 7px
    left: 7px
  & input
    margin-left: 46px
    width: 100%
    height: inherit
    outline: none
    &::-webkit-input-placeholder
      font:
        size: 14px
        weight: 400
      line-height: 18px
      color: #9B9B9B
    &::-moz-placeholder
      font:
        size: 14px
        weight: 400
      line-height: 18px
      color: #9B9B9B
    &:-moz-placeholder
      font:
        size: 14px
        weight: 400
      line-height: 18px
      color: #9B9B9B
    &:-ms-input-placeholder
      font:
        size: 14px
        weight: 400
      line-height: 18px
      color: #9B9B9B
.select
  border: 1px solid #C4C4C4
  background: url('../static/input/ic_up.svg') no-repeat right 10px center
  background-size: 16px 15px
  display: flex
  align-items: center
  padding-left: 15px
  width: 190px
  cursor: pointer
  & p
    line-height: 18px
    font-size: 14px
    margin-bottom: 0
.main
  display: flex
  flex-direction: column
  align-items: center
  background-color: #F7F6F4
  padding-top: 89px
.cards
  width: 1002px
  display: grid
  grid-template-columns: repeat(2, 1fr)
  grid-column-gap: 23px
  grid-row-gap: 23px
.bar
  width: 1002px
  display: flex
  justify-content: flex-start
  align-items: center
  padding-left: 25px
  padding-bottom: 20px
  padding-top: 32px
  &__container
    width: 411px
    height: fit-content
.checkbox_all
  display: flex
  align-items: center
.checkbox__label-all
  margin-left: 10px
  font:
    size: 13px
    weight: 400
  line-height: 20px
.buttons
  padding-left: 13px
  display: grid
  grid-column-gap: 10px
  grid-template-columns: repeat(3, 1fr)
</style>
