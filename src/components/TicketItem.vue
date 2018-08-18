<template>
  <div class="ticket">
    <div class="ticket__buy">
      <img class="ticket__carrier" src="@/assets/S7.png">
      <button type="button" class="ticket__button">Купить<br>за {{ticket.price}}₽</button>
    </div>
    <div class="ticket__info info">
      <div class="info__origin">
        <div class="info__time">{{ticket.departure_time}}</div>
        <div class="info__airport">{{ticket.origin}}, {{ticket.origin_name}}</div>
        <div class="info__date">{{ticket.departure_date}}</div>
      </div>
      <div class="info__stops stops">
        <p class="stops__text">{{ticket.stops > 0 ? `${ticket.stops} пересадка` : '&nbsp;'}} </p>
        <div class="stops__illustration">
          <div class="stops__line"></div>
          <img class="stops__plane" src="data:image/svg+xml;utf8;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iaXNvLTg4NTktMSI/Pgo8IS0tIEdlbmVyYXRvcjogQWRvYmUgSWxsdXN0cmF0b3IgMTYuMC4wLCBTVkcgRXhwb3J0IFBsdWctSW4gLiBTVkcgVmVyc2lvbjogNi4wMCBCdWlsZCAwKSAgLS0+CjwhRE9DVFlQRSBzdmcgUFVCTElDICItLy9XM0MvL0RURCBTVkcgMS4xLy9FTiIgImh0dHA6Ly93d3cudzMub3JnL0dyYXBoaWNzL1NWRy8xLjEvRFREL3N2ZzExLmR0ZCI+CjxzdmcgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIiB4bWxuczp4bGluaz0iaHR0cDovL3d3dy53My5vcmcvMTk5OS94bGluayIgdmVyc2lvbj0iMS4xIiBpZD0iQ2FwYV8xIiB4PSIwcHgiIHk9IjBweCIgd2lkdGg9IjE2cHgiIGhlaWdodD0iMTZweCIgdmlld0JveD0iMCAwIDUxMCA1MTAiIHN0eWxlPSJlbmFibGUtYmFja2dyb3VuZDpuZXcgMCAwIDUxMCA1MTA7IiB4bWw6c3BhY2U9InByZXNlcnZlIj4KPGc+Cgk8ZyBpZD0iZmxpZ2h0cyI+CgkJPHBhdGggZD0iTTUxMCwyNTVjMC0yMC40LTE3Ljg1LTM4LjI1LTM4LjI1LTM4LjI1SDMzMS41TDIwNCwxMi43NWgtNTFsNjMuNzUsMjA0SDc2LjVsLTM4LjI1LTUxSDBMMjUuNSwyNTVMMCwzNDQuMjVoMzguMjUgICAgbDM4LjI1LTUxaDE0MC4yNWwtNjMuNzUsMjA0aDUxbDEyNy41LTIwNGgxNDAuMjVDNDkyLjE1LDI5My4yNSw1MTAsMjc1LjQsNTEwLDI1NXoiIGZpbGw9IiNkMmQ1ZDYiLz4KCTwvZz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8L3N2Zz4K" />
        </div>
      </div>
      <div class="info__destination">
        <div class="info__time">{{ticket.arrival_time}}</div>
        <div class="info__airport">{{ticket.destination}}, {{ticket.destination_name}}</div>
        <div class="info__date">{{ticket.arrival_date}}</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ticket-item',
  props: {
    ticket: {
      type: Object,
      required: true
    }
  }
}
</script>

<style lang="scss" scoped>
.ticket {
  background: #fff;
  border-radius: 5px;
  box-shadow: 0 1px 4px 0 rgba(91, 137, 164, 0.25);
  margin-bottom: 20px;
  display: flex;

  &__buy {
    border-right: 1px solid #eceff1;
    padding: 20px;
    display: flex;
    flex-direction: column;
  }

  &__button {
    width: 160px;
    background: #ff6d00;
    box-shadow: 0 2px 1px 0 rgba(0, 0, 0, 0.1), 0 1px 0 0 #d64d08;
    border: none;
    color: #fff;
    border-radius: 5px;
    padding: 6px 30px;
    font-size: 1em;
    line-height: 1.4;
    cursor: pointer;

    &:hover {
      background: #ff8124;
      box-shadow: 0 1px 5px 0 rgba(0, 0, 0, 0.25), 0 1px 0 0 #f7661d;
    }
  }

  &__carrier {
    width: 120px;
    margin: 0 auto;
    margin-bottom: 10px;
  }

  &__info {
    display: flex;
    padding: 20px;
  }
}

.info {
  &__time {
    font-size: 2em;
    color: #4a4a4a;
    line-height: 1;
    padding-bottom: 5px;
  }

  &__airport {
    color: #4a4a4a;
    font-size: 0.75em;
  }

  &__date {
    color: #8b9497;
    font-size: 0.75em;
  }

  &__origin,
  &__destination {
    min-width: 110px;
  }

  &__destination {
    text-align: right;
  }
}

.stops {
  &__text {
    text-transform: uppercase;
    font-size: 0.625em;
    color: #8b9497;
    margin: 0;
    text-align: center;
  }

  &__illustration {
    display: flex;
    align-items: center;
  }

  &__line {
    display: block;
    width: 96px;
    height: 1px;
    background: #d2d5d6;
    margin-right: 1px;
  }

  &__plane {
    width: 13px;
    height: 13px;
  }
}
</style>

