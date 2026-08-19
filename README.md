# Bench 03: the price is in the URL, so it is not yours

Live: **https://michegz.github.io/price-in-the-url/**

A single-page bench you can run in thirty seconds with nothing installed.

The ordinary way to send a customer a prefilled payment form is to put the
quote in the link, mark the field hidden and read-only, and trust it on the way
back. Hidden and read-only are properties of a browser, not of your money.

The address bar on the page is editable. Change `basePrice` to anything, open
the form, authorize, and look at what the office sees. Then tick the box that
builds the charge server side and try the identical link.

## What it proves

With the price in the link, a $450 job can be authorized at $50 and every
artifact of the transaction looks correct: a genuine electronic signature, a
completed payment, a customer who agreed to the number on their screen. Nobody
has to notice until someone reconciles the job against the deposit.

Building the charge from the job record on the server closes it, and nothing in
the customer's browser had to change.

## What it does not prove

The page carries its own limits section in full. Short version: server-side
pricing is one control and not a payment security review; the signed-token
approach is the other valid fix and is not shown; the mismatch has to actually
reach a human; and a payment that succeeds while the confirmation fails is a
separate failure path.

## How it runs

No network calls, no card processor, no build step. One `index.html`. The
`resolveAmount` function is printed on the page from its own running source, so
the code you read cannot drift from the code that just ran.

Tested in headless Chrome at 1280px and 390px across five paths: the honest
authorization, a tampered link on the prefill build, the same tampered link on
the server-side build, an unparseable price, and a one-cent price. Zero console
errors.

## Honesty

Everything on the page is invented: the job number, the office, the customer,
the quote. No real business is represented and no claim is made about any
specific product. There is no news story attached to this bench and nothing in
it to fact check; it proves itself by running.

---

Built by Michelle W., automation engineer, Lafayette, Louisiana.
[Hire me on Upwork](https://www.upwork.com/freelancers/~01b59471ec1e32fbdb)

See also [Bench 01](https://michegz.github.io/guardrail-bench/) and
[Bench 02](https://michegz.github.io/agent-authz-bench/).
