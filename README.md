# @stencila/email-templates

These templates are intended to be used for transactional and marketing emails.

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

## Updating SendGrid

First run `npm run build` to generate the templates.
The following steps will change depending on which type of template you're creating. For:

### Transactional Template

Navigate to [SendGrid transactional templates](https://sendgrid.com/dynamic_templates/) and follow the [instruction here](https://sendgrid.com/docs/ui/sending-email/create-and-edit-legacy-transactional-templates/#creating-a-template).

> ⚠️ Please make sure to use the **Code Editor** mode as the type of template.

### Marketing Template

Navigate to [SendGrid marketing templates page](https://sendgrid.com/marketing_campaigns/ui/marketing_templates) and follow the [instruction here](https://sendgrid.com/docs/ui/sending-email/working-with-marketing-templates/#creating-a-new-template).

> ⚠️ Please make sure to use the **Design Editor** mode as the type of template.

You can see the existing templates by changing `Filter By` to `Custom`.

Once you’re in the template editor, follow the instructions for [Importing HTML into the template](https://sendgrid.com/docs/ui/sending-email/editor/#importing-custom-html-with-drag--drop-markup).

There are a few manual steps which need to be performed after each time HTML is imported:

- Change the `EMAIL BODY` `Background Color` to `#F5F5F5`
- Change the `EMAIL BODY` `Text Color` to `#363636`
- Change the `EMAIL BODY` `Link Color` to `inherit`
- Change the `EMAIL BODY` `Font Size` to `20px`
- Change the email `CONTENT CONTAINER` width to `640px`

## Sending Emails

Transactional Email templates require some [substitution tags](https://sendgrid.com/docs/ui/sending-email/how-to-send-an-email-with-dynamic-transactional-templates/#send-a-transactional-email) to be defined for the variables to be correctly interpolated.

Each template's requirements can be seen in a `<template-name>-data.json` file.
Please note that there are some additional requirements for the [transactional footer partial](./src/_partials/transactional/footer-data.json). and the [campaign footer partial](./src/_partials/campaign/footer-data.json).

## References

- [MJML Documentation](https://mjml.io/documentation)
- [SendGrid Editor Documentaiton](https://sendgrid.com/docs/ui/sending-email/editor/)
