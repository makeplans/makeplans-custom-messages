# MakePlans Custom Messages

## Get started

Emails and SMS sent from MakePlans can be customised and dynamically include relevant data. There are also texts shown on the booking site and in the administration system that can be customised in the same way.
The messages are generated using [Liquid](http://liquidmarkup.org). Please read the [Liquid documentation](https://github.com/Shopify/liquid/wiki) for more information. You can use HTML and all standard Liquid syntax.

In most cases you will reference the booking object, however there are some places where there is no booking context and you can reference the relevant object directly. For example in the footer of the booking site where you can reference the client object directly.

## Complete example

```
Hi {{ booking.person.name }}, you have booked {{ booking.resource.title }} on {{ booking.booked_from }}.
```

Usage without any booking context, for example in the booking site footer:
```
This is the booking site for {{ client.name }}. Enjoy!
```

## Available objects

* [Booking](#booking)
* [Person](#person)
* [Service](#service)
* [Event](#event)
* [Resource](#resoure)
* [Client](#client)

## Other user cases

* [Calendar](#calendar-event)
* [Locale](#locale)
* [Advanced usage](#advanced-usage)

### Booking

Example: `{{ booking.booked_from }}`

* id
* booked_from (localized)
* booked_to (localized)
* booked_from_iso8601
* booked_to_iso8601
* time_range (booked_from and booked_to)
* verification_code (for SMS verification)
* verification_link (for email verification)
* verification_method
* count
* notes
* custom_data
* link (for information about the booking)
* price
* title
* description
* price
* booking_capacity
* confrere_url (Confrere integration must be activated)
* zoom_url (Zoom integration must be activated)
* whereby_url (Whereby integration must be activated)

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
* description
* payment_required
* price
* custom_data

#### Event

Example: `{{ booking.event.title }}`

* id
* title (full title including event type title)
* event_title (title for the specific event without event type title)
* description (event type or specific event description)
* event_description (description for the specific event without event type description)
* payment_required
* price
* custom_data

#### Resource

Example: `{{ booking.resource.title }}`

* id
* title
* custom_data

#### Client

Example: `{{ booking.client.name }}`

* name
* subdomain
* domain
* address
* country
* country_code
* email
* phone_number
* currency
* verification_method

### Calendar event

You can use Liquid to dynamically generate the conents of an event displayed in the administration calendar. The associated object ([booking](#booking) or [event](#event)) is available, in addition you can use common standardised attributes.

Example: `{{ display_title }}{% if booking %} {{ booking.notes }}{% endif %}`

* all_day
* default_title (the full generated title, for example service title + event title)
* display_title (the default shown event text)
* end
* event_type (booking or event)
* object_title (the title of the booking or the event)
* start

### Locale

This is just an attribute, not an object. See [localisation](#localisation) for usage.

* locale

## Advanced usage

### Date formatting

For custom date/time formatting using the `_iso8601` fields see [usage of Liquid filters](https://docs.shopify.com/themes/liquid-documentation/filters/additional-filters#date) and [strfti.me](http://www.strfti.me) for date/time reference. In addition to the standard Liquid filters we have included `i18n_date` filter which works like the standard `date` filter but will output based on your account locale and time zone. The standard `date` filter will only output English.

Date filter examples:

`{{ booking.booked_from_iso8601 | i18n_date: '%A, %B %e, %Y' }}` will result in `Thursday, January 4, 2018`.

`{{ booking.booked_from_iso8601 | i18n_date: '%H:%M' }}` will result in `13:25`.

### Localisation (i18n)

You can use `locale` to render output based on language. For example:

```
{% if locale == 'nb' %}
Viking
{% else %}
Not viking
{% endif %}
```