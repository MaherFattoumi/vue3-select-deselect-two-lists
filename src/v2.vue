<template>
  <div>
    <select v-model="selectedItemOne" @change="updateListTwo">
      <option v-for="item in listOne" :value="item">{{ item }}</option>
    </select>
    <select v-model="selectedItemTwo" @change="updateListOne">
      <option v-for="item in listTwo" :value="item">{{ item }}</option>
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
    const selectedItemOne = ref('');
    const selectedItemTwo = ref('');

    const updateListTwo = () => {
      listTwo.value = [...originalListTwo].filter(item => item !== selectedItemOne.value);
      selectedItemTwo.value = listTwo.value.length > 0 ? listTwo.value[0] : '';
    };

    const updateListOne = () => {
      listOne.value = [...originalListOne].filter(item => item !== selectedItemTwo.value);
      selectedItemOne.value = listOne.value.length > 0 ? listOne.value[0] : '';
    };

    watch(selectedItemOne, () => {
      updateListTwo();
    });

    watch(selectedItemTwo, () => {
      updateListOne();
    });

    // Initialisation des sélections par défaut
    updateListTwo();
    updateListOne();

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
