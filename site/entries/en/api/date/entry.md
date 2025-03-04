---
title: Date
---

- [\Flextype\Component\Date\Date](#class-flextypecomponentdatedate)

<hr /><a id="class-flextypecomponentdatedate"></a>
### Class: \Flextype\Component\Date\Date

| Visibility | Function |
|:-----------|:---------|
| public static | <strong>days()</strong> : <em>array</em><br /><em>Get number of days. $months = Date::days();</em> |
| public static | <strong>daysInMonth(</strong><em>int/\integer</em> <strong>$month</strong>, <em>\integer</em> <strong>$year=null</strong>)</strong> : <em>int</em><br /><em>Returns the number of days in the requested month $days = Date::daysInMonth(1);</em> |
| public static | <strong>dos2unix(</strong><em>int/\integer</em> <strong>$timestamp</strong>)</strong> : <em>int</em><br /><em>Converts a DOS timestamp to UNIX format. $unix = Date::dos2unix($dos);</em> |
| public static | <strong>format(</strong><em>int/\integer</em> <strong>$date</strong>, <em>\string</em> <strong>$format=`'j.n.Y'`</strong>)</strong> : <em>int</em><br /><em>Get format date echo Date::format($date, 'j.n.Y');</em> |
| public static | <strong>hours(</strong><em>\integer</em> <strong>$step=1</strong>, <em>\boolean</em> <strong>$long=false</strong>, <em>\integer</em> <strong>$start=null</strong>)</strong> : <em>array</em><br /><em>Get number of hours, incrementing by a step. $hours = Date::hours();</em> |
| public static | <strong>minutes(</strong><em>\integer</em> <strong>$step=5</strong>, <em>int/\integer</em> <strong>$start</strong>, <em>\integer</em> <strong>$end=60</strong>)</strong> : <em>array</em><br /><em>Get number of minutes in a hour, incrementing by a step. $minutes = Date::minutes();</em> |
| public static | <strong>months()</strong> : <em>array</em><br /><em>Get number of months. $months = Date::months();</em> |
| public static | <strong>season()</strong> : <em>string</em><br /><em>Get current season name echo Date::season();</em> |
| public static | <strong>seconds(</strong><em>\integer</em> <strong>$step=1</strong>, <em>int/\integer</em> <strong>$start</strong>, <em>\integer</em> <strong>$end=60</strong>)</strong> : <em>array</em><br /><em>Get number of seconds in a minute, incrementing by a step. $seconds = Date::seconds();</em> |
| public static | <strong>timezones()</strong> : <em>array</em><br /><em>Get Time zones</em> |
| public static | <strong>today(</strong><em>\string</em> <strong>$format=`'m.d.y'`</strong>)</strong> : <em>string</em><br /><em>Get today date echo Date::today();</em> |
| public static | <strong>tomorrow(</strong><em>\string</em> <strong>$format=`'m.d.y'`</strong>)</strong> : <em>string</em><br /><em>Get tomorrow date echo Date::tomorrow();</em> |
| public static | <strong>unix2dos(</strong><em>int/\integer</em> <strong>$timestamp</strong>)</strong> : <em>int</em><br /><em>Converts a UNIX timestamp to DOS format. $dos = Date::unix2dos($unix);</em> |
| public static | <strong>years(</strong><em>\integer</em> <strong>$start=1980</strong>, <em>\integer</em> <strong>$end=2024</strong>)</strong> : <em>array</em><br /><em>Get number of years. $years = Date::years();</em> |
| public static | <strong>yesterday(</strong><em>\string</em> <strong>$format=`'m.d.y'`</strong>)</strong> : <em>string</em><br /><em>Get yesterday date echo Date::yesterday();</em> |
| protected static | <strong>_range(</strong><em>mixed</em> <strong>$step</strong>, <em>mixed</em> <strong>$start</strong>, <em>mixed</em> <strong>$end</strong>, <em>bool</em> <strong>$flag=false</strong>)</strong> : <em>void</em><br /><em>_range()</em> |
