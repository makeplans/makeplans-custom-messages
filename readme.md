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

* booked_from
* booked_to
* verificaion_code
* notes
* custom_data

#### Event

Example: `{{ booking.resource.title }}`

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
* phonenumber
* date_of_birth
* national_id_no
* street
* postal_code
* city
* state
* country_code
* custom_data

#### Service

Example: `{{ booking.service.title }}`

* title
* payment_required
* price
* custom_data