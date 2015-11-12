# MakePlans Custom Messages - Version 1.0

## Get started

Emails and SMS sent from MakePlans can be customised and also include relevant data. The messages are built with [Liquid](http://liquidmarkup.org). Please read the [Liquid documenation](https://github.com/Shopify/liquid/wiki) for more information. You can use HTML and all standard Liquid syntax.

## Complete example

```
Hi {{ booking.person.name }}, you have booked {{ booking.resource.title }} on {{ booking.booked_from }}.
```

## Available objects

### Booking

Example: `{{ booking.booked_from }}`

* id
* booked_from (localized)
* booked_to (localized)
* booked_from_iso8601
* booked_to_iso8601
* verificaion_code (for SMS verification)
* verification_link (for email verification)
* count
* notes
* custom_data
* link (for information about the booking)

#### Event

Example: `{{ booking.event.title }}`

* title
* payment_required
* price
* custom_data

#### Resource

Example: `{{ booking.resource.title }}`

* title
* custom_data

#### Person

Example: `{{ booking.person.name }}`

* name
* email
* phone_number (can also use the depreated phonenumber)
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

* title
* payment_required
* price
* custom_data