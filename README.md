# @stencila/email-templates

These templates are intended to be used for transactional and marketing
emails.

They are built using [MJML](https://mjml.io).

## Quick Start

There are two kinds of templates,
[Transactional](https://sendgrid.com/use-cases/transactional-email/) and
[Marketing Campaign](https://sendgrid.com/solutions/email-marketing/)
templates.

1. `git clone git@github.com:stencila/email-templates.git && cd email-templates`
2. `npm install`
3. `npm run start`

## Production Build

To build the templates for use with other services, run:

`npm run build`

This will generate two directories inside the `./dist`, one for email
campaigns for use with Intercom (`./dist/campaigns/`), and one for usage via the Stencila Hub and
SendGrid (`./dist/transactional/`).

## Media asset notes

Images for use inside the email body should be `576px` wide to avoid overflow
issues on some email clients.

## Updating Intercom marketing templates

First run `npm run build` to generate the templates.

As part of the build step the `npm run prepare:intercom` will do the
following:

- Add a [`data-premailer="ignore"`
  attribute](https://www.intercom.com/help/en/articles/245-a-guide-to-creating-html-emails#best-practices-for-using-html-in-intercom)
  to `<style>` tags to prevent Intercom from inlining them when sending a
  campaign. This is because we already inline the necessary styles during
  compilation of this project.
- There are some styles which need to be
  inlined, namely the dynamic content from the Intercom email editor, for those
  we look for the special `/* inline-styles */` comment, and replace it with a
  simple `<style type="text/css">` tag which will be inlined by Intercom.

Navigate to [Intercom email templates
page](https://app.intercom.com/a/apps/y554dhej/settings/email-templates)
paste in the contents of the generated `campagins/template-intercom.html`
file into the editor and save the template.

## Update Hub

_To be documented_

## Sending Transactional Emails via SendGrid API

Transactional Email templates require some [substitution
tags](https://sendgrid.com/docs/ui/sending-email/how-to-send-an-email-with-dynamic-transactional-templates/#send-a-transactional-email)
to be defined for the variables to be correctly interpolated.

Each template's requirements can be seen in a `<template-name>-data.json`
file. Please note that there are some additional requirements for the
[transactional footer
partial](./src/_partials/transactional/footer-data.json). and the [campaign
footer partial](./src/_partials/campaign/footer-data.json).

## References

- [MJML documentation](https://mjml.io/documentation)
- [Intercom email template documentation](https://www.intercom.com/help/en/articles/245-a-guide-to-creating-html-emails)
- [SendGrid Editor documentation](https://sendgrid.com/docs/ui/sending-email/editor/)
