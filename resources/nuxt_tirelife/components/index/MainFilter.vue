<template>
  <div class="main__filter">
    <div class="main__filter-tabs">
      <div class="main__filter-wrap">
        <button class="main__filter-tab" :class="activeTab ? 'main__filter-tab-active' : 'main__filter-tab-nonactive'" @click="clickTab('Tires')">Шины</button>
        <button class="main__filter-tab" :class="!activeTab ? 'main__filter-tab-active' : 'main__filter-tab-nonactive'" @click="clickTab('Disks')">Диски</button>
      </div>
    </div>
    <div class="main__filter-selects">
      <div class="main__filter-select" v-if="activeTab" v-for="(select, i) in filterTires">
        <Select
          @parentSelectHandler="selectTire"
          :active="select.active"
          :keyBitch="i"
          :params="select.params"
          :word="select.name"
          :classActive="['custom-select__arrow_black-active', 'custom-select__arrow_black']"
          :className="'custom-select_white'"
        />
      </div>
      <div class="main__filter-select" v-if="!activeTab" v-for="(select, i) in filterDisks">
        <Select
          @parentSelectHandler="selectDisk"
          :active="select.active"
          :params="select.params"
          :keyBitch="i"
          :word="select.name"
          :classActive="['custom-select__arrow_black-active', 'custom-select__arrow_black']"
          :className="'custom-select_white'"
        />
      </div>
    </div>
    <div class="main__filter-btn f-end">
      <Button :word="'подобрать'" :width="'w-200'" :fz="'f-18'"/>
    </div>
  </div>
</template>

<script>
import Button from "../common/Button";
export default {
  components: {Button},
  data: () => ({
    arrowState: 'black',
    filterTires: [
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
    filterDisks: [
      {
        name: 'Ширина',
        params: [12, 33, 44, 93, 54],
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
        name: 'Вылет',
        params: [
          19, 20, 21, 23, 35,
        ],
        active: false
      },
      {
        name: 'DIA',
        params: [
          19, 20, 21, 23, 35,
        ],
        active: false
      },
      {
        name: 'Болты',
        params: [
          19, 20, 21, 23, 35,
        ],
        active: false
      },
      {
        name: 'PCD',
        params: [
          19, 20, 21, 23, 35,
        ],
        active: false
      },
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
    doActiveList(arr, activeKey) {
      arr.forEach((el, i) => {
        if (i === activeKey && el.active) {
          el.active = !el.active
        } else {
          el.active = i === activeKey
        }
      })
    },
    selectTire(key){
      this.doActiveList(this.filterTires, key)
    },
    selectDisk(key){
      this.doActiveList(this.filterDisks, key)
    },
    clickTab(tab){
      this.activeTab = tab === 'Tires' ? true : false
    }
  }
}
</script>
