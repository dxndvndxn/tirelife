<template>
  <div class="custom-select" @click="selectHandler" :class="className">
    {{ word }}
    <span class="custom-select__arrow" :class="active ? classActive[0] : classActive[1]"></span>
  </div>
</template>

<script>
export default {
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
      type: Number
    },
    active: {
      type: Boolean
    }
  },
  methods: {
    selectHandler(){
      this.$emit('parentSelectHandler', this.keyBitch)
    }
  }
}
</script>
