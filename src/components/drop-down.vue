<template>
  <div class="dropdown" ref="refDropDown">
    <a href="#" class="btn btn-outline-light my-2 dropdown-toggle" @click.prevent="toggleOpen">
      {{ title }}
    </a>
    <ul class="dropdown-menu" :style="{ display: 'block' }" v-if="isOpen">
      <slot></slot>
    </ul>
  </div>
</template>
<script lang="ts">
import { defineComponent, watch, ref } from 'vue'
import useClickOutside from '../hooks/use-click-outside'
export default defineComponent({
  name: 'DropDown',
  props: {
    title: {
      type: String,
      required: true
    }
  },
  setup() {
    const isOpen = ref(false) // ref()：将括号内值变成响应式对象
    const refDropDown = ref<null | HTMLElement>(null) // vue3中获取dom节点的方法，注意，命名要和template中ref的命名一样
    const toggleOpen = () => {
      isOpen.value = !isOpen.value
    }
    const isClickOutside = useClickOutside(refDropDown) // 判断点击事件是否在组件外

    watch(isClickOutside, () => {
      if (isOpen.value && isClickOutside.value) {
        isOpen.value = false
      }
    })

    return {
      isOpen,
      refDropDown,
      toggleOpen
    }
  }
})
</script>
<style></style>
