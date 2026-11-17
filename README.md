# CPCS Renewals Portal: Card Holder Slice (Prototype)

A rough first slice of a renewals portal for the CPCS card scheme, built in about 30 minutes for the NOCN Full-Stack Developer interview workshop.

> **Prototype only.** All data is fictional mock data. There is no real authentication, backend or personal data.

**Live link / repo:** [add link]

---

## 1. The problem as I understand it

CPCS cards expire and must be renewed with the right evidence. Without a valid card, an operator can't work on site. The brief says renewals are failing for three reasons:

1. Reminders aren't arriving.
2. People get stuck partway through renewing online.
3. Everyone rings NOCN to find out where things are.

The common thread is **visibility**: people can't see what they need to do or where their renewal is, so they phone.

---

## 2. Why I chose this slice first: the card holder's "My Renewal" page

I started with the card holder because they are the person directly affected by the failing renewals. If the card holder can't see their expiry date, what evidence is missing and where their renewal is up to, then the employer and centre views will just show the same confusion to more people.

The page answers one question at a glance: **"Where is my renewal and what do I need to do next?"**

It includes:
- Expiry date and days remaining, with clear states (not relying on colour alone)
- One prominent "what you need to do next" action
- An evidence checklist with a status for each item
- A renewal progress timeline
- A "send a message" option, so help can happen in the portal rather than by phone

The three scenarios (switchable with a dev-only dropdown) are: expiring soon with evidence missing, under review, and approved with a new card on its way.

---

## 3. Questions I'd ask before building

I'd start the workshop with these. Where I've made an assumption, I've written it below so we can correct it together.

### Understanding the renewal process
1. **What does a card holder need to renew a CPCS card?** Which qualifications or certificates, and do they differ by card type?
2. **What test is involved and what is the pass mark?**
3. **How is evidence checked today?** Manually by staff, or automatically? How long does it take?
4. **Where in the online journey do people get stuck?** Do we know the exact step?

### Reminders
5. **Why weren't reminders arriving?** Out-of-date contact details, emails going to spam, or no reminder being sent? If the portal doesn't fix the cause, we could build it well and still miss the problem.
6. **Which channels do card holders actually use?** Email, text or phone? Many will be on site on a mobile.

### Users and data
7. **How does a card holder prove who they are?** Card number, date of birth, something else?
8. **Where does renewal data live today, and can we access it** (API, database or manual export)?
9. **What can employers and centres see about an individual, and on what basis (GDPR)?**

### Success and priorities
10. **What does success look like for the pilot?** Fewer calls, more on-time renewals, or revenue retained?
11. **Who pays the renewal fee**, the card holder or the employer? That affects who the portal should serve first.
12. **What are the top reasons people ring today?** Which calls would we most like to remove?
13. **Are there accessibility needs or an existing design system I should follow?**

---

## 4. My assumptions (to confirm in the workshop)

These are my starting guesses and may well be wrong:

- A card holder needs a recognised **qualification showing they can operate the machine** (for example an NVQ or equivalent), plus a **test** to show their knowledge.
- There is a **minimum pass mark** for the test. I assumed around 50%, but I don't know the real figure and it may differ by card type.
- The card holder **uploads proof** of their result or qualification.
- Once the evidence is **verified**, the renewal can be processed and the new card issued.
- Most card holders use a **mobile phone**, so I've designed mobile first with plain English.
- Mock data stands in for the real renewal data until I know where it lives.

---

## 5. What I deliberately left out (and why)

- **Real authentication.** I'd design this properly with the team, not generate it quickly.
- **Backend and integrations.** I need answers to the data questions first.
- **Employer and centre views.** These are next (see below).
- **Reminders.** Not built in this slice, but see next steps.
- **Payment.** Out of scope for the first slice.

---

## 6. Next steps

1. **Employer team view (next slice).** Employers see their whole team's cards and renewals at a glance: who is due soon, what is missing and the current status. This helps them plan who can work on site, spot people who haven't acted, and nudge them. *To validate:* whether employers need this to schedule shifts, and what personal data they are allowed to see.
2. **Reliable reminders.** Email or text with a link straight to the card holder's renewal page, once I understand why the current ones fail.
3. **Real login and data.** Secure authentication and a connection to the real renewal data, with data protection checked from the start.
4. **Centre view.** Renewals that training and test centres are helping with.
5. **In-portal messaging.** Built after I've seen what people actually ask, so I'm not building a chat tool nobody needs.
6. **Measure it.** Track call volume, on-time renewals and where people drop off, to see whether the pilot works.

---

## 7. How I used AI

- **Tool:** v0 (and [other tools, e.g. Claude, Cursor]).
- **What I asked it to do:** generate the page structure, components and mock data from a detailed prompt.
- **What I checked or changed:**
  - [e.g. Reworded text that wasn't plain English]
  - [e.g. Added icons and text labels so status isn't shown by colour alone]
  - [e.g. Removed any fields or features I hadn't asked for]
  - [e.g. Checked it on a phone-sized screen]
- **What I chose not to use AI for:** authentication design, the choice of what to build first, and decisions about what personal data to show.

---

## 8. How I'd build and host it

- **Stack:** Next.js (App Router), TypeScript and Tailwind CSS.
- **Hosting:** Azure Static Web Apps or Azure App Service for the prototype, moving to a proper environment once real data is involved.
- **Production approach:** secure authentication, an API layer over the renewal data, automated tests on critical paths and CI/CD.

---

## Run locally

```bash
npm install
npm run dev
```

Then open http://localhost:3000.
