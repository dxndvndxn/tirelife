<template>
  <div class="main__filter">
    <div class="main__filter-tabs">
      <div class="main__filter-wrap">
        <button class="main__filter-tab" :class="activeTab ? 'main__filter-tab-active' : 'main__filter-tab-nonactive'" @click="clickTab('Tires')">Шины</button>
        <button class="main__filter-tab" :class="!activeTab ? 'main__filter-tab-active' : 'main__filter-tab-nonactive'" @click="clickTab('Disks')">Диски</button>
      </div>
    </div>
    <div class="main__filter-selects">
      <div class="main__filter-select" v-for="(select, i) in filterData">
        <Select
          @parentSelectHandler="selectHandler"
          :active="select.active"
          :keyBitch="i"
          :word="select.name"
          :classActive="['custom-select__arrow_black-active', 'custom-select__arrow_black']"
          :className="'custom-select_white'"
        />

      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    arrowState: 'black',
    filterData: [
      {
        name: 'Ширина',
        params: [
          255, 190, 175, 250, 295
        ],
        active: false,
      },
      {
        name: 'Высота',
        params: [
          55, 40, 35, 54, 50
        ],
        active: false
      },
      {
        name: 'Диаметр',
        params: [
          19, 20, 21, 23, 35,
        ],
        active: false
      },
      {
        name: 'Сезон',
        params: [
          'Лето',
          'Зима',
          'Зима',
          'Демисезон'
        ],
        active: false
      }
    ],
    activeTab: true
  }),
  computed: {
    receiveArrState: {
      get(){
        return this.arrowState
      },
      set(newArrState){
        return newArrState
      }
    }
  },
  methods: {
    selectHandler(key){
      this.filterData[key].active = !this.filterData[key].active
    },
    clickTab(tab){
      this.activeTab = tab === 'Tires' ? true : false
    }
  }
}
</script>
