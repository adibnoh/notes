# Datetime

Currently the best Javascript plugin for Date manipulation is [Luxon](https://moment.github.io/luxon/#/)

## Duration in human

This snippet require us to import new plugin [Humanize Duration](https://github.com/EvanHahn/HumanizeDuration.js)

```javascript

const DateTime = luxon.DateTime;
const Interval = luxon.Interval;

const start = DateTime.fromSQL("2020-06-19 11:14:00");
const finish = DateTime.fromSQL("2020-06-21 13:11:00");

const formatted = Interval
    .fromDateTimes(start, finish)
    .toDuration()
    .valueOf();

console.log(humanizeDuration(formatted))
console.log(humanizeDuration(formatted, { language: 'es' }))
console.log(humanizeDuration(formatted, { language: 'ru' }))

```

[https://stackoverflow.com/a/65651515](https://stackoverflow.com/a/65651515)