<template>
  <transition-group name="list" tag='div' class="container notification-container">
    <div class="row" v-for="each in collection" v-bind:key="each.id">
      <NotificationChild :item="each"/>
    </div>
  </transition-group>
</template>

<!-- // // // //  -->

<script>
import NotificationChild from './NotificationChild'

export default {
  computed: {
    collection () {
      return this.$store.getters['notification/collection']
    }
  },
  components: {
    NotificationChild
  }
}
</script>

<!-- // // // //  -->

<!-- QUESTION - SCOPED? -->
<style>

  .container-fluid.notifications {
    position: fixed;
    z-index: 999;
    width: 50%;
    right: 0;
    bottom: 0;
    margin-top: 7.5rem;
    margin-bottom: 3rem;
    margin-right: .5rem;
  }

  .list-enter-active, .list-leave-active {
    transition: opacity .1s;
  }

  .list-enter, .list-leave-to {
    opacity: 0;
  }

</style>
