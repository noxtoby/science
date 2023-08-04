---
title: "Data-driven computational models of familial Alzheimer's disease"
date: "2018-01-29"
categories: 
  - "work"
---

> \[UPDATE\] The published version is available here: [Brain 141(5), awy050 (2018)](https://academic.oup.com/brain/advance-article/doi/10.1093/brain/awy050/4951528?guestAccessKey=73f004ae-2bcc-47aa-b1b5-c94e563084ea).
> 
> "The paper is a pleasure to read, as well as scientifically insightful." — Journal Editor

My latest paper on Alzheimer's disease progression has been accepted in [Brain](http://academic.oup.com/brain). The preprint is on bioRxiv, available for free:

> Data-driven models of dominantly-inherited Alzheimer's disease progression Neil Oxtoby, Alex(andra) Young, Dave Cash, Tammie Benzinger, Anne Fagan, John Morris, Randy Bateman, Nick Fox, Jon Schott, Danny Alexander [bioRxiv, 250654 (2018)](http://doi.org/10.1101/250654)

Familial AD (known more technically as "dominantly-inherited" AD or "autosomal dominant" AD) is very rare cause of dementia - about 1% of all AD. It's caused by one of a family of genetic mutations inherited (50/50 chance) from a parent, and results in developing [AD symptoms](http://en.wikipedia.org/wiki/Alzheimer's_disease#Signs_and_symptoms) (memory loss, etc.), earlier than usual - in your 40s or 50s, rather than 60s or 70s.

Because this rare disease is dominantly inherited, it's possible to identify people who carry one of the genetic mutations before symptoms appear. These people are usually recruited via their parents, after their parents have been diagnosed. This presymptomatic phase enables us to study familial AD progression before it's too late, which is impractical for typical, non-familial AD (you'd need to observe many thousands of people, annually, over 10-20 years or more, and many of these wouldn't develop AD). Further, during this pre symptomatic phase of familial AD it's possible to estimate the number of years until the onset of symptoms in mutation carriers, called "EYO" (Estimated Years to Onset). This is because children often develop symptoms around the same age as their parents do: usually within about 5 years of the same age.

So, EYO represents a good, but not great, method/model for "staging" patients along the timeline of familial AD progression.

We wanted to see if data-driven disease progression modelling could do better.

In this paper, we analysed biomarker data including brain imaging data (MRI and PET), specific protein levels in spinal fluid, and scores on a cognitive test to build computational models of the sequence and timing of familial AD progression (specifically, [event-based models](http://neiloxtoby.com/work/2014/08/event-based-model-of-alzheimers-disease/) and differential equation models). The data came from a global collection of volunteer participants including families affected by familial AD (parents and their adult children) in the [DIAN](http://dian-info.org) dataset.

Our models do not use EYO (the current state of the art), and we predicted symptom onset more accurately than using EYO (within 1.3 years, compared to 5.5 years for EYO in our experiments).

Another win for computational, data-driven modelling of neurological diseases!

Next step: apply similar approaches to other diseases, and combine what we learn with the aim to produce a useful tool for identifying people at risk well before the disease has taken hold.

The paper is in production over at [Brain](http://academic.oup.com/brain) and should be available soon.
