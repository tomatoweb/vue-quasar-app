<template>

  <div class="my-component bg-deep-purple-5 text-white q-pa-md rounded">imported component</div>

</template>

<script>

import { defineComponent } from 'vue'

export default defineComponent({
  name: 'MyComponent'
})

</script>

<style>
.my-component{
  border-radius: 5px;
}
</style>