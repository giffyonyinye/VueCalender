<template>
    <div class="calendar">
        <div class="year">
          <!-- {{startDay()}} -->
            <p class="current-month">{{currentMonthName}}</p>
            <p class="current-month">{{currentYear}}</p>

        </div>
        <div class="days">
            <p v-for="day in days" :key="day">{{day}}</p>
        </div>

        
        <div class="num">
            <p v-for="num in startDay()" :key="num"></p>
            <p v-for="num in daysInMonth()" :key="num" :class="currentDateClass(num) ">{{num}}</p><div class="num">

        </div>

        </div>

        <div style="display:flex; justify-content:space-between">
            <button @click="prev">Prev</button>
            <button @click="next">Next</button>
        </div>
    </div>
    
</template>


<script>
export default {
    data() {
        return{
            currentDate : new Date().getUTCDate(),
            currentMonth: new Date().getMonth(),
            currentYear: new Date().getFullYear(),
            days: ['Sun', 'Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat']
        }
    },

    methods: {
        daysInMonth() {
            return new Date(this.currentYear, this.currentMonth + 1, 0).getDate()
        },

        startDay() {
            return new Date(this.currentYear, this.currentMonth, 1).getDay();
        },

        prev() {
            if(this.currentMonth === 0 ) {
                this.currentMonth = 11;
                this.currentYear--
            }else {
            this.currentMonth--
            }
        },

        next() {
            if(this.currentMonth === 11) {
                this.currentMonth = 0
                this.currentYear ++
            } else {
            this.currentMonth++

            }
        },

        currentDateClass(num) {
            const calendarFullDate = new Date(this.currentYear, this.currentMonth, num).toDateString();
            const currentFullDate = new Date().toDateString()
            return calendarFullDate === currentFullDate ? 'exactdate' : '';
        }
    },

    computed: {
        currentMonthName() {
            return new Date(this.currentYear, this.currentMonth).toLocaleString('default', {month: 'long'})
        }
    }
}
</script>

<style scoped>
.days {
    display: flex;
    padding-left: 2rem;
}
.days p {
   width: 14.28%;
    text-align: center;
}

.num {
    display: flex;
    padding-left: 2rem;
    flex-wrap: wrap;
}

.num p{
    width:14.28%;
    text-align: center;
    padding: .3rem;
}

.calendar {
    width: 30rem;
    padding-top: 2rem;
}

.current-month {
    padding-left: 2rem;
    font: bold;
}

.year {
    display: flex;
    justify-content: space-between;
    padding: 2rem;
}

.exactdate {
    background-color: grey;
}
</style>