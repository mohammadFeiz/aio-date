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
- #### pattern is optional(if set pattern result will be string else result will be array)
