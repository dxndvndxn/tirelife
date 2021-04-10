<template>
  <div class="custom-select" :class="className">
    <div class="custom-select__wrap f-bet" @click="selectHandler">
      <span class="custom-select__word">{{ word }}</span>
      <span class="custom-select__arrow" :class="active ? classActive[0] : classActive[1]"></span>
    </div>
    <transition enter-active-class="showList" leave-active-class="hideList">
      <ul class="custom-select__list" v-if="active">
        <li class="custom-select__item" v-for="(param, i) in params" :key="i" @click="setActiveItem(param)">
          <span class="custom-select__child" :class="{'custom-select__child_active': activeItemsList.find(activeParam => activeParam === param)}"> {{ param }} </span>
        </li>
      </ul>
    </transition>
  </div>
</template>

<script>
export default {
  data: () => ({
    activeItemsList: []
  }),
  props: {
    word: {
      type: String
    },
    className: {
      type: String
    },
    classActive: {
      type: Array
    },
    keyBitch: {
      type: Number,
      default: null
    },
    active: {
      type: Boolean
    },
    params: {
      type: Array
    }
  },
  methods: {
    selectHandler(){
      this.$emit('parentSelectHandler', this.keyBitch)
    },
    setActiveItem(activeItemList) {
      let findActive = this.activeItemsList.find(el => el === activeItemList)

      if (findActive) {
        this.activeItemsList = this.activeItemsList.filter(el => el !== activeItemList)
        return
      }

      this.activeItemsList.push(activeItemList)
    }
  }
}
</script>
