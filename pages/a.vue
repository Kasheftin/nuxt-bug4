<template>
  <TwoColumns>
    <input v-model="str"> {{str}}
  </TwoColumns>
</template>

<script>

import TwoColumns from '~/components/TwoColumns'

export default {
  components: {
    TwoColumns
  },
  data () {
    return {
      str: ''
    }
  }
}

</script>
