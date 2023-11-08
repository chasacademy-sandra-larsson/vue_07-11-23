<template>
  <ChildComponent :message="message" @button-click="handleClick"  />

  <ul>
    <ShoppingItem v-for="(item, index) in shoppingList" :item="item" :key="item.id"
      :class="{active: item.isActive}"
      @selected-grocery="toggleItem(index)" 
    />
  </ul>
  <br>
  <CustomButton :class="btnClass" @custom-btn-clicked="handleCustomButtonClicked">
          <span>Contact {{ userName }}</span>
    </CustomButton>

</template>

<script langt="ts">
import ChildComponent from '@/components/ChildComponent.vue'
import ShoppingItem from '@/components/ShoppingItem.vue'
import CustomButton from '@/components/CustomButton.vue'
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'App',
  components: {
     ChildComponent,
      ShoppingItem,
      CustomButton
  },
  emits: ['click', 'selected-grocery', 'custom-btn-clicked'],
    data() {
    return {
      message: 'Hello World',
      shoppingList: [
        { id: 1, text: 'Vegetables', isActive: false},
        { id: 2, text: 'Cheese',  isActive: false},
        { id: 3, text: 'Potatoes', isActive: false},
        { id: 4, text: 'Whatever else humans are supposed to eat', isActive: false }
      ],
      btnClass: "primary",
      userName: "John Doe"
    }
  },
  methods: {
    handleClick() {
      console.log('Click happened in child component')
    },
    toggleItem(index) {
      this.shoppingList[index].isActive = !this.shoppingList[index].isActive
    },
    handleCustomButtonClicked() {
      console.log("clicked in custombutton")
    }
  }
})
</script>

<style scoped>
header {
  line-height: 1.5;
}


</style>
