---
title: "Doxa: The Memory Indian Doctors Never Had"
date: "2026-05-30"
tags: ["healthcare", "ai", "startups", "india", "ambient-ai"]
excerpt: "Why I'm building Doxa, an AI medical memory layer for India's 800,000 paper-based clinics, where doctors see 40 patients a day and remember none of them after they walk out."
---

It's late. I just got back from sitting inside a clinic in a Tier-2 Indian town watching a doctor see 38 patients in four hours. Forty seconds of eye contact. A scribbled prescription on a half-torn pad. "Come back in three days." Next patient. Repeat. Repeat. Repeat.

That doctor will not remember any of those 38 people tomorrow morning. Not their names, not what he prescribed, not who he told to come back. The paper leaves with the patient. The memory leaves with the patient. And in 72 hours when nobody walks back through the door, he won't even know who didn't return.

This is the reality of Indian outpatient care for roughly **800,000 clinics**. And we are building Doxa to fix it.

## The problem nobody in healthtech wants to look at

Everyone building "AI scribes" right now is building for a 30-minute American appointment in an air-conditioned room with a laptop on the desk and Epic in the browser. Abridge. Nabla. Ambience. Beautiful products. Completely useless for the doctor I just watched.

Indian outpatient consultations are **3 minutes long**. The doctor will not type. The doctor will not put a tablet between himself and the patient. The doctor will not "integrate with the EMR" because there is no EMR. There is a pen, a pad, and a memory that's already overflowing by 11am.

Practo tried. DocPlix tried. Every Indian healthtech that tried to "digitize the clinic" failed because they attacked the wrong artifact. **The prescription paper was never the problem.** The 20-second handwritten Rx is actually a beautiful piece of design, it's fast, it's tactile, the patient trusts it, the chemist reads it. Trying to kill paper is trying to kill the workflow that lets a doctor see 40 patients a day in the first place.

The problem is what happens *after* the patient walks out. The memory disappears. And with it, around **₹50,000 a month per clinic** in follow-ups that never happen because nobody remembered to call.

## What Doxa actually is

Doxa is not an EMR. I keep saying this because I need it to be loud: **we are not building an EMR.**

We are building the memory layer that sits on top of the existing paper workflow without touching it.

The doctor sees the patient like he always has. Writes the paper like he always has. Hands it over in 20 seconds like he always has. Then, after the patient leaves, he taps his phone and speaks for fifteen seconds:

> "Amit, 34, fever three days, viral, PCM 500 BD five days, follow-up 31st."

That's it. Our AI structures that voice memo into a real medical record, patient, age, symptoms, diagnosis, medicines with dosage, follow-up date. At the end of the day the doctor swipes through forty entries in two minutes and confirms. Next morning his phone tells him: *eight follow-ups due today, three chronic patients overdue.* The SMS goes out automatically. The patient comes back. The doctor recovers the revenue that was always silently leaking out the door.

Zero typing. Zero workflow change. Zero seconds added to the patient's wait time. Fifteen seconds, once, after they leave.

## Why this works in India when it can't work anywhere else

The whole AI scribe wave is happening because ambient transcription finally works. But "ambient" assumes a quiet room and a long appointment. Indian clinics are loud, fast, code-mixed, and chaotic. So we flipped the constraint: don't try to listen ambiently, give the doctor a 15-second post-consultation micro-interaction he can actually do.

And we're training on **Hinglish medical voice**, the actual language doctors think in. *"BP 120 by 80, sugar 110, fever hai, PCM do BD mein, 3 din baad aana."* No global AI scribe handles this. None of them will, because they're optimizing for Kaiser Permanente, not for a single-doctor clinic in Jaipur. That dataset gap is our moat.

## Why I'm doing this

I grew up around this. I've watched doctors in my family run clinics where the most sophisticated piece of technology is a thermometer. I've watched them lie awake worried about a medico-legal case where their only defense is a one-line scribble on a piece of paper from three years ago. I've watched them genuinely forget patients they've seen 12 times and feel ashamed about it.

These are some of the smartest, hardest-working people I know. They don't need a 50-feature dashboard. They need their memory back.

The bigger picture, the one that keeps me up: if we get this right, Doxa becomes the first time Indian primary care has structured data at all. Which means we become the first time you can actually manage diabetes and hypertension at the primary care level in this country at scale. India has the largest preventive healthcare opportunity on the planet sitting on top of the world's largest paper trail. We want to be the layer that turns that paper into signal.

## Where we are

We're a small team. We're embedding in clinics. We're shipping fast, the loop is build, sit in a clinic for two hours, watch a doctor use it, ship a fix the same evening. We're picking our first cohort of doctors as design partners, not customers.

If you're a doctor running a small clinic and any of this sounds like your life, I want to hear from you. If you're an engineer who wants to build voice and AI for a market that nobody else is taking seriously, I want to hear from you. If you're an investor, an operator, a clinic owner, a med-rep, a chemist, a patient with strong opinions, same thing.

Find me on Twitter/X. The DMs are open. We're not building an EMR. We're building the memory Indian doctors never had.

More soon.
