<template>
  <!-- Don't drop "q-app" class -->
  <div id="q-app">

      
      <router-view></router-view>
  </div>
</template>

<script>
import { QTransition } from 'quasar'
export default {
  components: {
    QTransition
  }
}
</script>

<style lang="stylus">
@import '~variables'

main
  text-align center
  margin-top 40px

</style>
