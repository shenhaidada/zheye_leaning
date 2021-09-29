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
import { defineComponent, onMounted, onUnmounted, ref } from 'vue'
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

    const handler = (e: MouseEvent) => {
      if (refDropDown.value) {
        if (!refDropDown.value.contains(e.target as HTMLElement) && isOpen.value) {
          isOpen.value = false
        }
      }
    }

    onMounted(() => {
      document.addEventListener('click', handler)
    })
    onUnmounted(() => {
      document.removeEventListener('click', handler)
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
