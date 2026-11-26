# Discovery results — current email request contract

The canonical questionnaire is https://ziontechgroup.com/discovery/.

## Live implementation

The public page:

1. validates the answers and participant email in the browser;
2. creates the on-screen recommendations and text summary immediately;
3. sends the same summary to FormSubmit, addressed to `commercial@ziontechgroup.com` with the participant in `_cc`;
4. reports explicit provider acceptance, refusal or an uncertain result;
5. blocks automatic duplicate submission for the same summary during the page session; and
6. offers a manual email fallback when delivery cannot be confirmed.

The current public flow does **not** use a Zion SMTP backend, repository dispatch retry, durable `leads/` append or guaranteed-delivery workflow. Do not publish those claims unless a deployed implementation and recipient-level evidence exist.

## Verification contract

Use only controlled Zion data for tests. Record a non-client test identifier and keep these states distinct for each recipient:

- **On-screen result generated**
- **Request accepted by FormSubmit**
- **Message delivered to participant mailbox**
- **Message delivered to Commercial mailbox**
- **Bounce or refusal**

A FormSubmit success response is not inbox-delivery proof. A message received by one mailbox with both addresses in its headers is not independent evidence for the other mailbox. Re-send only the missing recipient after reconciling the test identifier and current delivery state.

## Privacy and operations

Do not put customer data, credentials, SMTP settings or confidential results in repository files, issues, workflow logs or public artifacts. The questionnaire is free; paid work, prices, checkout and implementation remain separate.
