# MakePlans Custom Messages - Version 1.0

## Get started

Emails and SMS sent from MakePlans can be customised and also include relevant data. The messages are built with [Liquid](http://liquidmarkup.org). Please read the [Liquid documentation](https://github.com/Shopify/liquid/wiki) for more information. You can use HTML and all standard Liquid syntax.

## Complete example

```
Hi {{ booking.person.name }}, you have booked {{ booking.resource.title }} on {{ booking.booked_from }}.
```

## Available objects

* [Booking](#booking)
* [Person](#person)
* [Service](#service)
* [Event](#event)
* [Resource](#resoure)

### Booking

Example: `{{ booking.booked_from }}`

* id
* booked_from (localized)
* booked_to (localized)
* booked_from_iso8601
* booked_to_iso8601
* verification_code (for SMS verification)
* verification_link (for email verification)
* count
* notes
* custom_data
* link (for information about the booking)

For custom date/time format using the `_iso8601` fields see [usage of Liquid filters](https://docs.shopify.com/themes/liquid-documentation/filters/additional-filters#date).

#### Person

Example: `{{ booking.person.name }}`

* id
* name
* email
* phone_number (can also use the deprecated phonenumber)
* phone_number_formatted (E.164 formatted phone number with plus sign, international code, and no spaces or parentheses)
* date_of_birth
* national_id_no
* street
* postal_code
* city
* state
* country_code
* country
* custom_data

#### Service

Example: `{{ booking.service.title }}`

* id
* title
* payment_required
* price
* custom_data

#### Event

Example: `{{ booking.event.title }}`

* id
* title
* payment_required
* price
* custom_data

#### Resource

Example: `{{ booking.resource.title }}`

* id
* title
* custom_data