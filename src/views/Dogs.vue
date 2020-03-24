<template>
    <div>
      <b-table striped hover :items="items"></b-table>
    </div>
</template>

<script>
import dogs from '@/data/dogs.js'
export default {
  data () {
    return {
      dogs
    }
  }
}
</script>
