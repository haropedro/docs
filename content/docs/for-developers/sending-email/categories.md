---
layout: page
weight: 0
title: Categories
group: x-smtpapi
navigation:
  show: true
---

<call-out type="warning">

This information will be stored as a “Not PII” field and may be used for counting or other operations as SendGrid runs its systems. These fields generally cannot be redacted or removed. You should take care not to place PII in this field. SendGrid does not treat this data as PII, and its value may be visible to SendGrid employees, stored long-term, and may continue to be stored after you’ve left SendGrid’s platform.

</call-out>

You can add [categories]({{root_url}}/glossary/categories/) to the X-SMTPAPI header of the emails you send via SendGrid. This will allow you to track emails based on your own categorization system.

<call-out type="warning">

Categories must be in 7bit encoding using the US-ASCII character set.

</call-out>

<call-out>

Currently, there is no limit to the number of categories you can track. However, we recommend _no more than ~100 total unique categories_ as this will increase your ease of use in the Statistics area. Additionally, a high rate of unique categories on your account can negatively impact the rate at which we process the messages you send.

</call-out>

## Example

You can use SendGrid's [SMTP API]({{root_url}}/ui/for-developers/sending-email/getting-started-smtp/) to add these categories to your email. The following should be added to the email's header:

<call-out type="warning">

When passing `category` please make sure to only use strings as shown in our examples. Any other type could result in unintended behavior.

</call-out>

### Example Category Header

```json
{
  "category": "Example Category"
}
```

In this example, SendGrid would associate statistics for the email containing that header with the category **Example Category**.

## Limitations

You can assign up to 10 categories per message:

```json
{
  "category": ["dogs", "animals", "pets", "mammals"]
}
```

<call-out type="warning">

Categories should be used to group messages together by broad topic. If you need to attach unique data or identifiers to a message, use [Unique Arguments]({{root_url}}/for-developers/sending-email/unique-arguments/) instead.

</call-out>
