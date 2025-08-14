<script>

import { ref } from 'vue'
import MyComponent from '../components/MyComponent.vue';

export default {
  components: {
    MyComponent
    },
  setup () {
    return {
      count: ref(0)
    }
  }
}

</script>

<template>

  <div class="q-pa-xl column inline items-center q-gutter-lg">
    <button
      @click="count++">You clicked me {{ count }} times.
    </button>
    <MyComponent />
  </div>


</template>