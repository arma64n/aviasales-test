<template>
  <div id="app" class="app">
    <aside class="app__filter">
      <tickets-filter ></tickets-filter>
    </aside>
    <main class="app__tickets">
      <ticket-item 
      v-for="ticket in tickets" 
      :key="ticket.arrival_time"
      :ticket="ticket"
      :currency="currency"
      >
      </ticket-item>
    </main>
  </div>
</template>

<script>
import TicketsFilter from '@/components/TicketsFilter'
import TicketItem from '@/components/TicketItem'
import json from '@/assets/tickets.json'

export default {
  name: 'app',
  components: {
    TicketsFilter,
    TicketItem
  },
  data() {
    return {
      tickets: null,
      currency: 'rub'
    }
  },
  created() {
    this.tickets = JSON.parse(JSON.stringify(json.tickets))
  }
};
</script>

<style lang="scss">
.app {
  margin-top: 60px;
  width: 800px;
  margin: 0 auto;
  display: flex;

  &__filter {
    width: 200px;
  }

  &__tickets {
    display: flex;
    flex-direction: column;
  }
}
</style>
