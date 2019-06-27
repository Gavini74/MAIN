# Glossary


This is a placeholder for the MAIN glossary of terms.

## A
#### A/B Testing
In the context of MAIN, it is the ability to provide publications with the option to test two different variants of the same functionality. For example it could randomly assign 50% of traffic to one experience and 50% of traffic to another so that half the audience gets the article for free and half do not. The publication would then look to see which variant performed best for the given scenario, in this case probably conversion to a subscription.

#### ACS (Access Control System)
Handles both Authenticaton (authn) and Authorization (authz) for TNL. The "join pages" (those hosted at join.thetimes.co.uk) handle account creation and login (authn), when a product is purchased the entitlement is also handled by ACS and joined to the given identity. It also manages the original marketing permissions that are being replaced by Permission Centre.

The TNL websites are behind Akamai where ACS performs "auth at the edge", essentially saying "yes" or "no" to Akamai's question of "Am I entitled to see this article?". If they are not entitled, they are sent to the teased version otherwise they are sent to the non-teased version of the article.

#### ADE (Access Decision Engine)
A piece of code that determines whether the requested entity (e.g. an article) for a given user can be viewed by them or not. It's effectively the software for a paywall.

#### Ad-hoc entitlement
The ability to grant an entitlement to a user dynamically at any time. This could be a conscious decision by the publication, through ML or because of some other trigger. This is sometimes called a "Dynamic Paywall"

#### Agnostic
Any third party we add should be abstracted by our platform making it "agnostic" of the underlying tool. If we were to change that tool it is ok to make a breaking change to the publisher (as a last resort) but not ok to effect end users.

#### Akamai
Acts as a Content Delivery Network (CDN) that serves the majority of web traffic at News UK. For most websites your content does not change overly frequently and is not personalised to a single user, this allows the site to use a CDN to cache resources and serve the same article to person B as it just gave to person A without having to do "too much" work, making the site faster and cheaper. It can also be distributed globally so a person in the U.S. doesn't have to be hit by the latency of contacting servers in Ireland.



As well as this aspect, Akamai is used to filter out Bot traffic, segment traffic, for "auth at the edge" (see ACS) as well as for protection against many attack vectors.


#### AI
Prefer the term "ML" which is more specific to the work being performed as a tangible subset of AI. AI is very broad in scope and shifts with trends whereas we're likely to use some form of reinforcement learning to tune barrier pages for example.

#### Auth0 Agnostic
maiden-identity should support all user requirements (login/acc. creation/SSO etc.) without affecting the end user if it were to no longer use Auth0. It is acceptable to making a breaking change to our direct customer, the publisher.

## B
#### Barrier Page
Sometimes incorrectly referred to as a paywall, can be a modal, interstitial or some other treatment but effectively disrupts the user with a personalised proposition, encouraging up-selling/cross-selling or some other selling opportunity.

#### Bundle
An entitlement to a collection of entities such as articles grouped by topic or label.

#### BYOP
Bring your own PIM. Maiden at its core is headless but for some users (marketing/product) they'll need a UI to configure it. For the creation of products to sell we may want to recommend a PIM with out of the box integrations though it doesn't form part of the core product.



## C
#### Customer
The user of Main, in this case it's a "publication". Also see "tenant"



## D
#### Dogfood
 Dogfooding allows employees to test their company's products in real-life situations; a perceived, but still controversial, advantage beyond marketing, which gives management a sense of how the product might be used—all before launch to consumers.



#### Dwell Time
The amount of time spent on an entity (usually an article) which indicates engagement with the content.

#### Dynamic Paywall
The ability to change a user's entitlements on an ad hoc basis e.g. the paywall may be moved/removed depending on behaviour.



## E
#### Engine
Usually used to represent built code by the internal team that forms part of News' IP rather than software which has been bought from a third-party. It should have a clear set of capabilities which it provides. It's distinctive from the UI which is interchangeable and largely remains intact through time even though iterated on.



#### Entitlement
An entity that represents access to a piece of content. This could be a singular thing such as an interactive or a tree of things like an Edition. It may also come with various clauses such as an expiry date or metering.
#### Entitlement Group
The foundation of a proposition, taking the raw building blocks (entitlements) and composing them into something that you would sell such as the "Sport Section" which is an entity of "Section" faceted by "Sport". May include time clauses.



## F
#### Fail (Open/Closed)
If there is a bug or a service integral to the paywall is down, there are generally speaking two options, "fail open" and "fail closed". "Fail open" takes the paywall down for everyone regardless of who they are, this protects commercial revenue and can reduce customer complaints while it's being fixed. However, it may reduce payments because you've lost an instrument to push people into the funnel. "Fail closed" is the opposite, it protects the brand and it's premium status while it's being fixed but may offer a greatly reduced service resulting in complaints.

#### Flexible Paywall
A hard paywall is one in which all traffic must be authenticated before access can be granted. This has the advantage of being considerably harder to avoid and much easier for a publication to attach behaviour and personalisation to a given user. If anonymous users are given some content for free before hitting the paywall, the metering effectively creates a flexed paywall and can depend on the user, running experiments or pre-configured behaviour.



## G
#### Gamification
The ability to increase engagement by providing incentives for people to consume a publication through a reward based system.



## H
#### Householding
The ability to attach several different people to a single login, like Netflix, so that people can share their entitlements (within a family say) but still benefit from a personalised experience.


## I
#### IAM - Identity, Access, Monetisation
A generic umbrella term for the three pillars, can be used as a catchall term of capabilities or to explain Main, but prefer Main if referring to the product we're building.

#### Idle time
The time between the request for an entity and when it is considered the visit for a user has ended. This is used by ADE to determine which view budget to deduct the requested entity from. Typically this would be used to provide different lifetime experiences for a user and allowing them 5 mins to read an article before it's considered that they've moved away and will be starting again as a fresh visit.



#### Ingest
The process of taking output from a CMS and turning it into a publication specific data structure to support the given product.



## J


## K


## L
#### Lifetime
A collection of visits made by an anonymous user thereby giving them a pseudonymous identifier. Within these visits behaviour can be captured for use in experiments and giving a certain customer experience



## M
#### Maiden
A generic project name that represents the whole platform from an engineering perspective (including 3rd parties), covering Identity, Access and Monetisation.

(Monetisation Access Identity Decision Engine).

#### MAIN (Monetisation, Access and, Identity for News)
The product name for the IAM PaaS solution that we're building. Use this when referring to the product or it's specific capabilities (in uppercase to avoid ambiguity)

#### Metering
The ability to read a number of articles for free until the given number of units have been depleted (each unit being a unique article). The number of allowed units is refreshed at a known frequency such as weekly on a Monday.

#### ML Machine Learning
Taking large amounts of user data, segmenting it and deriving hypothesise to experiment on the various segments for feedback and tweaking of the original hypothesise.

#### MTTR (Mean Time To Repair)
The average of the time elapsed between a production incident occurring (separate to being raised) and the incident being contained or resolved with full functionality for our clients

#### Multi-armed bandit
An advanced form of A/B testing where many variants are provided to a user and fine tuned with ML until the optimum option is found and selected by diverting more and more traffic to the "winning" variant.

#### MVT
Multivariate Testing is much like A/B testing but with more letters. As a capability MAIN needs to provide MVT "out of the  box" for a publication to experiment with potential ideas. For example, with a flexible paywall, it may want to test 3-5 different experiences and measure which is best, this can also be used in conjunction with a multi-armed bandit test with online retraining of an ML model with a barrier page



## N
#### News coin
A crypto-currency that can be used to gain access to content behind the paywall. Can be earned in a variety of ways such as sharing, attending events, commenting, being an engaged user, viewing commercial products etc.

#### Next Best Action
A personalised action based on the user's behaviour suggested to the publication at any point in time. This could be in response to a page view with a recommended article or in response to an access denial with a recommended barrier page.



## O
#### Offer
Not to be confused by "Proposition", an offer is specifically a reduction in price attached to a proposition such as "30% off" or "was £3 now £1"

#### One Tap
You only login once, a Google initiative similar to social login/SSO.



## P
#### Passwordless
The ability to login without typing in a password such as a fingerprint or magic email link.

#### Payment Engine
Provides the ability for publications to take money for a product and backs-off onto a payment gateway or a product like Stripe. Can typically be seen as agnostic glue code that provides a common payment interface.

#### Paywall
A digital representation that signifies a lack of entitlement. This may be rendered as truncated text or some other manifestation.

#### PIM
Product Information Management - the process for handling all the data, content, and other material that is needed to market and sell products. IAM will communicate with PIM systems for marketing content etc.

#### Platform as a Service (PaaS)
A PaaS typically makes it much easier for a customer to develop, run and manage their software needs by abstracting away the infrastructure and development lifecycle to provide well documented and easy to use capabilities "off-the-shelf". In the context of MAIN publications may need all, most or just some of the capabilities provided and are free to pick the ones they need. The code in Global GitHub can be forked and stood up as a customer sees fit for them to run independently too rather than using the hosted solution provided by News UK.

#### Product
A proposition with attached assets (such as imagery, a strapline, CTA) that can be delivered to a specific audience (usually via a barrier page).

#### Product Engine
The software capabilities to create exotic products and business models for publications to experiment with and would include barrier page content and product specific emails. Typically a UI would lay over the top to allow a publication's non-developers to create the aforementioned.

#### Proposition
Entitlement group + price + payment medium + Ts & Cs. The basis of what is sold but without the human presentation or delivery attached to it.

#### Publication
Usually a single business such as "Harper Collins" but could be an off-shoot such as "TLS" or "Dream Team", or a product such as "TalkSport". A publication for MAIN is a single customer irrespective of it's structure which could be within News Corp or potentially outside it. SSO and bundled products can/may cross publications but each one has a specific identity, roadmap, features of MAIN it would like to use and hence would act as it's own tenant.

## Q


## R
#### Reference Model
An example client that uses the platform as intended, this could be a website or any other suitable user. It has many uses including; being a reference for other developers, as documentation, for demos, for "dogfooding" the APIs, for R&D of new ideas, for testing.

#### Refresh date
 When configuring a lifetime within ADE a publication may want to refresh the view budgets they've provided for the user on a recurring frequency using the "refresh interval". If for example the configuration is 5,1,0, a refresh date could be set with a 1 month refresh interval. While the user will only receive 6 article views in their first two visits, after 1 month they'll be able to have another 6 across two further visits and so on.

It can also be used to refresh a view budget by time to give recurring views independent of visits, for example 3 views per month refreshed each month regardless of visit.

The timer starts from the creation of the lifetime and has no bearing on the visit number.



## S
#### SSO - Single sign-on
The ability to login in one place with a single account but have entitled access across sites other than the one you logged into e.g. logging in to Okta as a News employee will also show you logged in to The Times with the appropriate staff access.

#### Subscriber
This term should be used carefully and sparingly due to it's loaded meaning and it's ability to derail the mind shift that we're trying to create. It is right to call a genuine subscriber a subscriber as in, a person who makes a recurring payment for a product, but that is not all users/and or all products. If using a general term, prefer customer, potential customer or anonymous user.

## T
#### Tealium
The primary "customer data collection" tool used at News UK. Usually added to publication clients by the Insights team where they refine and collate the data before storing in Big Query. See https://tealium.com/ for info.

#### Tenant
For Main it's a "publication" or "customer" but usually used to refer to the use of Main as a piece of software. The tenant will have it's own configuration, resource requirements, analytics, financials etc.

#### Title
Prefer "Publication" as it's less ambiguous



## U


## V
#### Value Exchange
Traditionally a fiscal exchange (you pay money) is made but potentially watching a video, filling a survey, looking at an advert could "unlock" content.

#### View budget
A typical configuration of the ADE for anonymous users will be a lifetime with a pattern of visits and their view budgets. Within each visit a user will be allowed to view an entity (article) that number of times before access is denied. When the visit ticks over and a fresh budget starts, access will again be granted and so on.

#### Visit
Currently this specifically relates to an anonymous user due to the term "session" being heavily overloaded and has connotations with authenticated users. A visit lasts from the first request to view an entity (such as an article) until the configured time has elapsed. This essentially allows a publication to configure the "idle time" for an anonymous user before it's deemed that they've "ended their visit". Each time the same entity is requested before the idle time has elapsed, the idle timer starts again, for example if it's set to 10 mins for an article, a user has up to 10mins to read each article before their view is counted as a subsequent visit



## W
#### Wallet
An online account that contains News coins that can be exchanged for products/services.



## X


## Y
#### Yolo
See "One Tap" above.



## Z