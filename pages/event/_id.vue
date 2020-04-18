<template>
  <div>
    <h1>Event #{{ id }}</h1>
  </div>
</template>

<script>
export default {
  data() {
    return {
      id: this.$route.params.id
    }
  },
  head() {
    return {
      title: `Event #${this.id}`,
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'All the information about the event ' + this.id
        }
      ]
    }
  }
}
</script>

<style lang="scss" scoped></style>
