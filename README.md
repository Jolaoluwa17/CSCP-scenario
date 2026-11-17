# CPCS Renewals Portal: Card Holder Slice (Prototype)

A rough first slice of a renewals portal for the CPCS card scheme, built in about 30 minutes for the NOCN Full-Stack Developer interview workshop.

> **Prototype only.** All data is fictional mock data. There is no real authentication, backend or personal data.

**Live link / repo:** https://cpcs-psi.vercel.app

---

## 1. The problem as I understand it

CPCS cards expire and must be renewed with the right evidence. Without a valid card, an operator can't work on site. The brief says renewals are failing for three reasons:

1. Reminders aren't arriving.
2. People get stuck partway through renewing online.
3. Everyone rings NOCN to find out where things are.

The common thread is **visibility**: people can't see what they need to do or where their renewal is, so they call us (NOCN).

---

## 2. Why I chose this slice first: the card holder's "My Renewal" page

I started with the card holder because they are the people directly affected by the failing renewals. If the card holder can't see their expiry date, what evidence is missing and where their renewal is up to, then the card holders will not know when they need to renew their cards to work.

The page answers one question at a glance: **"Where is my renewal and what do I need to do next?"**

It includes:
- Expiry date and days remaining, with clear states (not relying on colour alone)
- One prominent "what you need to do next" action
- An evidence checklist with a status for each item
- A renewal progress timeline
- A "send a message" option, so help can happen in the portal rather than by phone

Rather than switching between fixed scenarios, the prototype simulates the renewal journey itself. The card holder starts with a card that is expiring soon and evidence missing, then moves through the process: they submit their evidence, the renewal goes under review, and it is approved with a new card on its way. At each stage the next action, checklist and timeline update. The review and approval steps are simulated, because there is no real backend.

---

## 3. Questions I'd ask before building

I'd start the workshop with these. Where I've made an assumption, I've written it below so we can correct it together.

### Understanding the renewal process
1. **What does a card holder need to renew a CPCS card?** Which qualifications or certificates, and do they differ by card type?
2. **What test is involved and what is the pass mark?**
3. **How is evidence checked today?** Manually by staff, or automatically? How long does it take?
4. **Where in the online journey do people get stuck?** Do we know the exact step?

### Reminders
5. **Why weren't reminders arriving?** Out-of-date contact details, emails going to spam, text messages not sent or no reminder being sent at all? If the portal doesn't fix the cause, we could build it well and still miss the problem.
6. **Which channels do card holders actually use mostly?** Is it email or text? Many will be on site on a mobile.

### Users and data
7. **How does a card holder prove who they are?** Card number, date of birth, something else?
8. **What can employers and centres see about an individual, and on what basis (GDPR)?**

### Success and priorities
9. **Are there accessibility needs or an existing design system I should follow?**

---

## 4. My assumptions (to confirm in the workshop)

These are my starting guesses and may well be wrong:

- A card holder needs a recognised **qualification showing they can operate the machine** (for example an NVQ or equivalent), plus a **test** to show their knowledge.
- There is a **minimum pass mark** for the test. I assumed around 50%, but I don't know the real figure and it may differ by card type.
- The card holder **uploads proof** of their result or qualification.
- Once the evidence is **verified**, the renewal can be processed and the new card issued.
- Most card holders use a **mobile phone**, so I've designed mobile first with plain English.
- Mock data stands in for the real renewal data.

---

## 5. What I deliberately left out (and why)

- **Real authentication.** I'd design this properly with the team, not generate it quickly.
- **Backend and integrations.** I need answers to the data questions first.
- **Employer and centre views.** These are next (see below).
- **Reminders.** Not built in this slice, but see next steps.

---

## 6. Next steps

1. **Employer team view (next slice).** Employers see their whole team's cards and renewals at a glance: who is due soon, what is missing and the current status. This helps them plan who can work on site, spot people who haven't acted, and nudge them. *To validate:* whether employers need this to schedule shifts, and what personal data they are allowed to see.
2. **Centre view.** Renewals that training and test centres are helping with.
3. **In-portal messaging.** Built after I've seen what people actually ask, so I'm not building a chat tool nobody needs.

---

## 7. How I used AI

- **Tool:** v0 and claude.
- **What I asked it to do:** generate the page structure, components and mock data using various prompts detailed prompt.
- **What I checked or changed:**
  - Made sure the system was simple to use
  - Verified that the flow and process i wanted was what was generated
  - Removed any fields or features I hadn't asked for
  - Checked it on a phone-sized screen
- **What I chose not to use AI for:** the choice of what to build first.

---

## 8. How I'd build and host it

- **Stack:** Next.js (App Router), TypeScript and Tailwind CSS.
- **Hosting:** The frontend is deployed on Netlify, served from my existing domain, and the backend runs on Fly.io. Netlify acts as the public entry point for the frontend and talks to the Fly.io backend over HTTPS. 
- **Production approach:** secure authentication, an API layer over the renewal data, automated tests on critical paths and CI/CD.

---

## Run locally

```bash
npm install
npm run dev
```
