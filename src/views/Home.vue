<template>
  <div class="container">
    <div class="calendar">
      <div class="head">
        <div class="head__time">{{ momentTime }} </div>
        <div class="head__month">{{ momentTime2 }}</div>
      </div>
      <div class="days">
        <div class="days__btn">
          <h3 class="days__text">{{ month2 }} {{  }}</h3>
          <button class="arrow up"></button>
          <button class="arrow down"></button>
        </div>
        <div class="days__week"  v-for="day in week" :key="day">{{day}}</div>
        <div class="days__day" ></div>
      </div>
      <div class="today">
        <h2>Сегодня</h2>
        <input placeholder="Добавить событие или напоминание" type="text">
        <p>Нет событий</p>
      </div>
    </div>
  </div>
</template>

<script>
import moment from 'moment'

export default {
  name: 'Home',
  data() {
    return {
      month: new Date().getMonth(),
      year: new Date().getFullYear(),
      monthes: ["Январь","Февраль","Март","Апрель","Май","Июнь","Июль","Август","Сентябрь","Октябрь","Ноябрь","Декабрь"],
      week: ["Пн","Вт","Ср","Чт","Пт","Сб","Вс"],
      date: new Date(),
      month2: moment().format('LL'),
      momentTime: moment().format('LTS'),
      momentTime2: moment().format('MMMM  Do YYYY')
    }
  },
  methods: {
    getLastDay() {
      var year, month;
      var lastDay = new Date();

      if (arguments.length == 1) {
          lastDay = arguments[0];
      } else if (arguments.length > 0) {
          lastDay.setYear(arguments[0]);
          lastDay.setMonth(arguments[1]);
      }

      lastDay.setMonth(lastDay.getMonth() + 1);
      lastDay.setDate(0);

      return lastDay;
    }
  },
  computed: {
    
  }
  
}
</script>
