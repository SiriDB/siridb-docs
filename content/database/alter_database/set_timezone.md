---
title: "set timezone"
weight: 95
---

Change the timezone for the database. When using a date/time in a query, SiriDB
needs to convert the given date to a timestamp. Default **NAIVE** is used which
means SiriDB is naive about the time zone and acts as if it's a local time.

>**Warning**
>
>When using a SiriDB database over multiple time zones it's probably best to
>set the time zone to anything other than *NAIVE* since with *NAIVE* the server
>*receiving* the query will convert the date to a local time-stamp. This means that
>sending the same query to a server in another time zone could respond with
>a different result.
>
>However, it's always possible in the query to specify
>a UTC date by adding 'Z' to the date. For example: '2016-01-11 16:00Z' will
>use UTC as it's time zone, no matter what time zone the database has configured.

For a list of valid time zones see [timezones](../timezones).

### Examples

	# Set the default time zone to UTC
	alter database set timezone 'UTC'

	# Set the default time zone to NAIVE
	alter database set timezone 'NAIVE'

	# Set the default time zone to Europe/Amsterdam
	alter database set timezone 'Europe/Amsterdam'
