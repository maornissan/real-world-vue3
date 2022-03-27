<template>
  <div class="events">
    <EventCard v-for="event in events" :key="event.id" :event="event" />
  </div>
</template>

<script>
import EventCard from '@/components/EventCard'
import EventService from '../../services/EventService'
export default {
  name: 'Home',
  components: { EventCard },
  data() {
    return {
      events: null,
    }
  },
  created() {
    EventService.getEvents()
      .then((res) => {
        this.events = res.data
      })
      .catch((error) => console.log(error))
  },
}
</script>
<style>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
