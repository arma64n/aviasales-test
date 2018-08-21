<template>
  <div class="currency">
    <span class="currency__title">Валюта</span>
    <div>
      <ul class="currency__list">
        <li class="currency__item" 
        :class="{'currency__item--active': currency === current}" 
        v-for="currency in currencies" :key="currency"
        @click="setCurrency(currency)"
        >{{currency}}</li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'filter-currency',
  model: {
    prop: 'current',
    event: 'set-currency'
  },
  props: {
    current: {
      type: String,
      required: true
    }
  },
  data () {
    return {
      currencies: ['RUB', 'USD', 'EUR']
    }
  },
  methods: {
    setCurrency (x) {
      this.$emit('set-currency', x)
    }
  }
}
</script>

<style lang="scss" scoped>
.currency {
  width: inherit;
  font-size: 0.75em;
  font-weight: 600;

  &__list {
    display: flex;
    flex-wrap: nowrap;
    list-style: none;
    margin: 0;
    padding: 0;
    height: 40px;
  }

  &__item {
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    width: 33%;
    border: 1px solid #dce2e4;
    color: #2196f3;
    z-index: 1;

    &:first-child {
      border-radius: 5px 0 0 5px;
    }

    &:last-child {
      border-radius: 0 5px 5px 0;
    }

    &:not(:first-child) {
      margin-left: -1px;
    }

    &:not(&--active):hover {
      border: 1px solid #2196f3;
      background: #f2fcff;
      color: #2196f3;
      z-index: 2;
    }

    &--active {
      background: #2196f3;
      color: #fff;
      border: 1px solid #2196f3;
    }
  }
}
</style>
