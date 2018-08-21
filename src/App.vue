<template>
  <div id="app" class="app">
    <aside class="app__filter">
      <filter-currency v-model="currency"></filter-currency>
    </aside>
    <main class="app__tickets">
      <ticket-item 
      v-for="ticket in filteredTickets" 
      :key="ticket.arrival_time"
      :ticket="ticket"
      :currency="currency"
      >
      </ticket-item>
    </main>
  </div>
</template>

<script>
import FilterCurrency from '@/components/FilterCurrency'
import TicketItem from '@/components/TicketItem'
import json from '@/assets/tickets.json'

export default {
  name: 'app',
  components: {
    FilterCurrency,
    TicketItem
  },
  computed: {
    filteredTickets () {
      return this.tickets.sort((a, b) => a.price - b.price)
    }
  },
  data() {
    return {
      tickets: null,
      currency: 'RUB'
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
  margin: 0 auto;
  display: flex;
  justify-content: center;

  &__filter {
    width: 230px;
    height: fit-content;
    background: #fff;
    padding: 20px 15px;
    border-radius: 5px;
    box-shadow: 0 1px 4px 0 rgba(91, 137, 164, 0.25);
    margin-right: 20px;
    display: flex;
    box-sizing: border-box;
  }

  &__tickets {
    display: flex;
    flex-direction: column;
  }
}
</style>
