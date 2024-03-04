<template>
  <div>
    <select v-model="selectedItemOne" @change="updateListTwo">
      <option v-for="(item, index) in listOne" :value="item" :key="index">{{ item }}</option>
    </select>
    <select v-model="selectedItemTwo" @change="updateListOne">
      <option v-for="(item, index) in listTwo" :value="item" :key="index">{{ item }}</option>
    </select>
  </div>
</template>

<script>
import { ref, watch } from 'vue';

export default {
  setup() {
    const originalListOne = ['A', 'B'];
    const originalListTwo = ['B', 'D', 'E'];
    const listOne = ref([...originalListOne]);
    const listTwo = ref([...originalListTwo]);
    const selectedItemOne = ref('A');
    const selectedItemTwo = ref('B');

    const updateListTwo = () => {
      listTwo.value = [...originalListTwo].filter(item => item !== selectedItemOne.value);
    };

    const updateListOne = () => {
      listOne.value = [...originalListOne].filter(item => item !== selectedItemTwo.value);
    };

    watch(selectedItemOne, () => {
      updateListTwo();
    });

    watch(selectedItemTwo, () => {
      updateListOne();
    });

    return {
      listOne,
      listTwo,
      selectedItemOne,
      selectedItemTwo,
      updateListTwo,
      updateListOne,
    };
  },
};
</script>
