<template>
  <div>
    <h1>{{ event.title }}</h1>
  </div>
</template>

<script>
import EventService from '~/services/EventService'
export default {
  async asyncData({ error, params }) {
    try {
      const { data } = await EventService.getEvent(params.id)
      return {
        event: data
      }
    } catch (e) {
      error({
        statusCode: 503,
        message: `Unable to fetch event #${params.id} at this time. Please try again later.`
      })
    }
  },
  data() {
    return {
      id: this.$route.params.id
    }
  },
  head() {
    return {
      title: `Event ${this.event.title}`,
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'All the information about the event ' + this.event.title
        }
      ]
    }
  }
}
</script>

<style lang="scss" scoped></style>
