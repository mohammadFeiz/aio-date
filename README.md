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
### date property of all functions can be:
- #### string ('2022/4/5/12/30/40/3') ('year/month/day/hour/minute/second/tenthsecond') (from year to any next value)
- #### iso date ('2015-03-25T12:00:00Z')
- #### array ([2022,4,5,12,30,40,3]) ([year,month,day,hour,minute,second,tenthsecond]) (from year to any next value)
- #### miliseconds date (16765675665656)
## toJalali
```javascript
let result = AIODate().toJalali({date:'2022/4/4'});
//result is [1401,1,15]

let result = AIODate().toJalali({date:'2022/4/4',pattern:'{year}/{month}/{day}'});
//result is '1401/1/15'

let result = AIODate().toJalali({date:'2022/4/4',pattern:'{weekDay} {day} {monthString} {year}'});
//result is 'دوشنبه 15 فروردین 1401'

let result = AIODate().toJalali({date:'2022/4/4/22/30',pattern:'{weekDay} {day} {monthString} {year} ساعت {hour}:{minute}'});
//result is "دوشنبه 15 فروردین 1401 ساعت 22:30"
```

- #### date is required (string | array | number)
- #### pattern is optional(if set pattern result will be string else result will be array)

## toGregorian
```javascript
let result = AIODate().toGregorian({date:'1400/2/2'});
//result is [2021,4,22] 

let result = AIODate().toGregorian({date:'1400/2/2',pattern:'{year}/{month}/{day}'});
//result is '2021/4/22' 

let result = AIODate().toGregorian({date:'1400/2/2',pattern:'{weekDay} {day} {monthString} {year}'});
//result is 'thursday 22 april 2021' 

let result = AIODate().toGregorian({date:'1400/2/2/22/30',pattern:'{weekDay} {day} {monthString} {year} {hour}:{minute}'});
//result is "THURSDAY 22 APRIL 2021 22:30" 
```

- #### date is required (string | array | number)
- #### pattern is optional (if set pattern result will be string else result will be array)

## getToday
```javascript
let result = AIODate().getToday({calendarType:'gregorian'});
//result is [2023,3,12,20,26,57,9]

let result = AIODate().getToday({calendarType:'gregorian',pattern:'{year}/{month}/{day} {hour}:{minute}'});
//result is '2023/3/12 20:26'

let result = AIODate().getToday({calendarType:'jalali'});
//result is [1401,12,21,20,26,57,9]

let result = AIODate().getToday({calendarType:'jalali',pattern:'{year}/{month}/{day} {hour}:{minute}'});
//result is '1401/12/21 20:26'
```

- #### calendarType is required ('gregorian' | 'jalali')
- #### pattern is optional (if set pattern result will be string else result will be array)

## getWeekDay
```javascript
let {weekDay,index} = AIODate().getWeekDay({date:'1401/5/7'});
//weekday is جمعه
//index is 6

let {weekDay,index} = AIODate().getWeekDay({date:'2023/6/6'});
//weekday is TUESDAY
//index is 2
```
- #### date is required (string | array | number)

## getDateByPattern
```javascript
let result = AIODate().getDateByPattern({
    {date:'2023/4/5',pattern:'{year}/{month}/{day} {weekDay}'}
});
//result is '2023/4/5 WEDNESDAY'

let result = AIODate().getDateByPattern({
    date:'2023/4/5',pattern:'{day} {monthString} {year} {weekDay}'
});
//result is '5 APRIL 2023 WEDNESDAY'

let result = AIODate().getDateByPattern({
    date:'2023/4/5/10/30',pattern:'{year}/{month}/{day} {hour}:{minute}'
});
//result is '2023/4/5 10:30'

let result = AIODate().getDateByPattern({
    date:[2023,4,5,10,30],pattern:'{year}/{month}/{day} {hour}:{minute}'
});
//result is '2023/4/5 10:30'
```

- #### date is required (string | array | number)
- #### pattern is required (string)
- #### result is an string

## convertToArray
```javascript
let result = AIODate().convertToArray({date:'2022/4/4'});
//result is [2022,4,4]

let result = AIODate().convertToArray({date:1432445566787});
//result is [2015,5,24,10,2,46,8]
```
- #### date is required (string | number)
- #### result is an array

## getTime
```javascript
let result = AIODate().getTime({date:'2022/4/5'});
//result is 1649100600000

let result = AIODate().getTime({date:'2022/4/5/10/30'});
//result is 1649138400000

let result = AIODate().getTime({date:[2022,4,5,10,30]});
//result is 1649138400000

let result = AIODate().getTime({date:'2015-03-25T12:00:00Z'});
//result is 1427268600000

let result = AIODate().getTime({date:1755555656665});
//result is 1755555656665

let result = AIODate().getTime({date:'1402/3/3'});
//result is 1684873800000
```

- #### date is required (string | number | array)
- #### result is a miliseconds date(number)

## compaire
```javascript
let result = AIODate().compaire({date:'2022/4/4',otherDate:'2022/7/10'});       
//result is 'less'

let result = AIODate().compaire({date:'2022/4/4',otherDate:'2022/2/10'})       
//result is 'greater'
                    
let result = AIODate().compaire({date:'2022/4/4',otherDate:'2022/4/4'})       
//result is 'equal'

let result = AIODate().compaire({date:'2022/4/4',otherDate:1700000000000})       
//result is 'less'

let result = AIODate().compaire({date:'2022/4/4',otherDate:[2022,2,10]})       
//result is 'greater'
```
- #### date is required (string | array | number)
- #### otherDate is required (string | array | number)
- #### result is 'less' or 'greater' or 'equal'

## getMonthDaysLength
```javascript
let result = AIODate().getMonthDaysLength({date:'2022/4'});
//result is 30

let result = AIODate().getMonthDaysLength({date:'2022/7/5'});
//result is 31

let result = AIODate().getMonthDaysLength({date:'1400/12'});
//result is 29

let result = AIODate().getMonthDaysLength({date:'1399/12'});
//result is 30
```
- #### date is required (string | array | number)
- #### result is an number


## getDelta
##### this function get 2 dates as parameter and return deffrence of those by object
```javascript
let result = AIODate().getDelta({date:'2023/4/5',otherDate:new Date().getTime()});
//result is 
//{
//  "day": 23,
//  "hour": 3,
//  "minute": 10,
//  "second": 57,
//  "tenthsecond": 9,
//  "type": "remaining"
//}

let result = AIODate().getDelta({
    date:'2023/4/5',
    otherDate:new Date().getTime(),
    pattern:'{day} : {hour} : {minute} : {second}'
});
//result is "23 : 3 : 10 : 57"

let result = AIODate().getDelta({date:new Date().getTime() + 23000,otherDate:new Date().getTime()});
//result is 
//{
//   "day": 0,
//   "hour": 0,
//   "minute": 0,
//   "second": 23,
//   "tenthsecond": 0,
//   "type": "remaining"
//}

let result = AIODate().getDelta({date:new Date().getTime() - 23000,otherDate:new Date().getTime()});
//result is 
//{
//   "day": 0,
//   "hour": 0,
//   "minute": 0,
//   "second": 23,
//   "tenthsecond": 0,
//   "type": "passed"
//}

let res = AIODate().getDelta({date:'1401/12/12',otherDate:new Date().getTime()});
//res is 
//{
//   "day": 9,
//   "hour": 20,
//   "minute": 49,
//   "second": 2,
//   "tenthsecond": 0,
//   "type": "passed"
//}
```

- #### date is required (string | array | number)
- #### otherDate is required (string | array | number)
- #### pattern is optional (if set pattern result will be an string)

## getNextTime
```javascript
let result = AIODate().getNextTime({
    date:'1400/2/2/22/30',
    offset:1.5 * 60 * 60 * 1000
});
//result [1400,2,3,0,0,0,0]

let result = AIODate().getNextTime({
    date:'1400/2/2/22/30',
    offset:1.5 * 60 * 60 * 1000,
    pattern:'{year}/{month}/{day} {hour}:{minute}'
});
//result is "1400/2/3 0:0"
```
- #### date is required (string | array | number)
- #### offset is required (number) (miliseconds)
- #### pattern is optional (string)

## getDatesBetween
```javascript
let result = AIODate().getdatesBetween({
    date:'2022/4/4',
    otherDate:'2022/7/10',
    step:48 * 60 * 60 * 1000,
    pattern:'{day} {monthString} {year}'
});       
//result is [
//  "6 APRIL 2022",
//  "8 APRIL 2022",
//  "10 APRIL 2022",
//  "12 APRIL 2022",
//  "14 APRIL 2022",
//  "16 APRIL 2022",
//  "18 APRIL 2022",
//  "20 APRIL 2022",
//  "22 APRIL 2022",
//  "24 APRIL 2022",
//  "26 APRIL 2022",
//  "28 APRIL 2022",
//  "30 APRIL 2022",
//  "2 MAY 2022",
//  "4 MAY 2022",
//  "6 MAY 2022",
//  "8 MAY 2022",
//  "10 MAY 2022",
//  "12 MAY 2022",
//  "14 MAY 2022",
//  "16 MAY 2022",
//  "18 MAY 2022",
//  "20 MAY 2022",
//  "22 MAY 2022",
//  "24 MAY 2022",
//  "26 MAY 2022",
//  "28 MAY 2022",
//  "30 MAY 2022",
//  "1 JUNE 2022",
//  "3 JUNE 2022",
//  "5 JUNE 2022",
//  "7 JUNE 2022",
//  "9 JUNE 2022",
//  "11 JUNE 2022",
//  "13 JUNE 2022",
//  "15 JUNE 2022",
//  "17 JUNE 2022",
//  "19 JUNE 2022",
//  "21 JUNE 2022",
//  "23 JUNE 2022",
//  "25 JUNE 2022",
//  "27 JUNE 2022",
//  "29 JUNE 2022",
//  "1 JULY 2022",
//  "3 JULY 2022",
//  "5 JULY 2022",
//  "7 JULY 2022",
//  "9 JULY 2022"
//]
                    
```
- #### date is required (string | array | number)
- #### otherDate is required (string | array | number)
- #### step is required (number) (miliseconds)

