# Discovery — live delivery flow and network links

## Current public flow

The canonical questionnaire is https://ziontechgroup.com/discovery/.

When a visitor submits it:

1. The browser generates the personalized resource shortlist and summary immediately.
2. The page sends one HTTPS request to FormSubmit. The primary recipient is `commercial@ziontechgroup.com`; the participant address is placed in `_cc` unless it is the same address.
3. A successful FormSubmit response means only that the provider accepted the request. It is not proof that either inbox received the message.
4. An explicit provider refusal enables a retry. A timeout or uncertain response is never retried automatically in the same page session.
5. The page offers a manual `mailto:` fallback containing the same summary.

There is no required meeting, payment or card. Discovery remains free and online.

## Evidence levels

- **Generated:** recommendations and summary appeared in the browser.
- **Accepted:** FormSubmit returned an explicit success response.
- **Delivered:** the target mailbox independently recorded receipt.
- **Bounced:** a delivery-status notification identified the failed recipient.

Record these states separately. Never describe provider acceptance or message headers as proof of independent delivery to every recipient.

## Canonical links

- Questionnaire: https://ziontechgroup.com/discovery/
- Homepage entry: https://ziontechgroup.com/
- Apps catalog: https://ziontechgroup.com/apps/
- Field-service evidence guide: https://ziontechgroup.com/apps/field-service-evidence-guide.html
- Cases: https://ziontechgroup.com/case-studies/
