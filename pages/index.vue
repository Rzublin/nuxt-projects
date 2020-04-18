<template>
  <div>
    <h1>Events</h1>
    <EventCard v-for="event in events" :key="event.id" :event="event" />
  </div>
</template>

<script>
import EventCard from '../components/EventCard.vue'
export default {
  components: { EventCard },

  async asyncData({ $axios, error }) {
    try {
      const { data } = await $axios.get(
        'https://my-json-server.typicode.com/Rzublin/placeholder-db/events'
      )
      return {
        events: data
      }
    } catch (e) {
      error({
        statusCode: 503,
        message: 'Unable to fetch events at this time. Please try again later.'
      })
    }
  },
  head() {
    return {
      title: 'List Events',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'List all the exciting events in your neighborhood'
        }
      ]
    }
  }
}
</script>

<style lang="scss" scoped></style>
