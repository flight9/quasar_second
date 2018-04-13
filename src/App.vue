<template>
  <!-- Don't drop "q-app" class -->
  <div id="q-app">
    <router-view />
  </div>
</template>

<script>
/*
 * Root component
 */
export default {
  mounted () {
    // zm: test current route
    // (this will not get correct value)
    console.info('App this router:', this.$router)
    console.info('App current route:', this.$route)

    // zm: construct a one-time watcher by LinusBorg
    // (this will get correct value)
    this.routeWatcher = this.$watch(
      function () { return this.$route },
      function (route) {
        if (route.name === 'Launch') {
          console.log('App watched route', this.$route)
          // this.authenticate() // or whatever
          this.routeWatcher() // this disables the watcher
        }
      }
    )
  }
}
</script>

<style></style>
