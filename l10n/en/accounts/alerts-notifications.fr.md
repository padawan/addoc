+++
url = "/accounts/system-dalertes/"
title = "Alert System"
layout = "man"
hidden = true
tags = [ "admin interface", "suspension" ]
+++

For many reasons, can an alert be triggered by our system and this is how it works:

- **open** the alert (by an event) with sending an email informing the user(s) concerned;
- **Reminder emails**;
- **expiry** of the alert (if no corrective action was taken) with a possible action.

## Alert types

### Inactivity

This type of alert only concerns _free plans_ and is intended not to encumber our infrastructure with abandoned accounts.

- trigger: lack of connection to [admin interface](https://admin.alwaysdata.com) for a number of days:
  - a profile with less than a year old must log in every 120 days;
  - a profile created between 1 and 4 years must connect every 6 months;
  - a profile with 4 years of age, 1 connection per year is required.
- solution: connect to the admin interface;
- expiry : suspension of inactive profile and its accounts.

### Financial situation irregular

- trigger: Negative balance (such as issuing an invoice);
- solution: set to have a higher balance or equal to zero;
- expiration: suspension of the relevant profile and its accounts.

### Domain expiration

- trigger: a domain will expire in X days;
- solution: renew domain;
- expiry : the domain will therefore expire in danger of becoming unavailable.

### Automatic domain renewal

- trigger: automatic domain renewal is active but the balance is insufficient OR no credit card / no bank account has been configured;
- solution: fund the prepaid account with a sufficient amount OR add a credit card / bank account automatically to the payment methods;
- expiration: this type of alert does not expire.

### Credit Card Expiration

- trigger: a credit card will expire in less than 31 days;
- solution: remove or update credit card;
- expiration: this type of alert does not expire.

### Account Migration

- trigger: an [migration](advanced/migrations) for an account is programmed;
- resolve: apply migration;
- expiration: migration will be applied automatically (not necessary on the same day of expiration).
