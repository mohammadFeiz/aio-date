# aio-date
## all calculations of dates (gregorian and jalali)

### instalation
```javascript
npm install aio-date
```

### use
```javascript
import AIODate from 'aio-date';
```

### toJalali
```javascript
let result = AIODate().toJalali({date:'2022/4/4'});
//result is [1401,1,15]

let result = AIODate().toJalali({date:'2022/4/4',pattern:'{year}/{month}/{day}'});
//result is '1401/1/15'

let result = AIODate().toJalali({date:'2022/4/4',pattern:'{weekDay} {day} {monthString} {year}'});
//result is 'دوشنبه 15 فروردین 1401'
```

- #### date is required
- #### pattern is optional(if set pattern result will be string else result will be array)

### toGregorian
```javascript
let result = AIODate().toGregorian({date:'1400/2/2'});
//result is [2021,4,22] 

let result = AIODate().toGregorian({date:'1400/2/2',pattern:'{year}/{month}/{day}'});
//result is '2021/4/22' 

let result = AIODate().toGregorian({date:'1400/2/2',pattern:'{weekDay} {day} {monthString} {year}'});
//result is 'thursday 22 april 2021' 
```

- #### date is required
- #### pattern is optional (if set pattern result will be string else result will be array)

### getToday
```javascript
let res = AIODate().getToday({calendarType:'gregorian'});
//res is [2023,3,12,20,26,57,9]

let res = AIODate().getToday({calendarType:'gregorian',pattern:'{year}/{month}/{day} {hour}:{minute}'});
//res is 2023/3/12 20:26

let res = AIODate().getToday({calendarType:'jalali'});
//res is [1401,12,21,20,26,57,9]

let res = AIODate().getToday({calendarType:'jalali',pattern:'{year}/{month}/{day} {hour}:{minute}'});
//res is 1401/12/21 20:26
```

- #### calendarType is required ('gregorian' | 'jalali')
- #### pattern is optional (if set pattern result will be string else result will be array)
