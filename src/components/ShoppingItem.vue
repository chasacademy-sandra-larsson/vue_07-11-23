<template>
  <li :class="{active: isActive}" @click="handleClick">{{ item.text }}</li>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import type { PropType } from 'vue';

interface ShoppingItem  {
    id: number,
    text: string,
    isActive?: Boolean
}

export default defineComponent({
  name: 'ShoppingItem',
  props: {
    item: {
      type: Object as PropType<ShoppingItem>,
      required: true
    },
    isActive: {
        type: Boolean,
        default: false
    }
  },
  methods: {
    handleClick() {
        this.$emit('selected-grocery',this.item.id)
        console.log(this.item.id)

    }
  }
})
</script>

<style scoped>
     .active {
        background-color: papayawhip;
        width: min-content;
     }

</style>
