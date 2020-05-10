# sameAs spec | DRAFT

:warning: working document, currently only for collecting ideas

The purpose of this document is to describe "sameAs", and detail some of the reuirements 
and expectation for how it will behave.

This will form a foundation for spec'ing possible implementations.

## The problem

In scuttlebutt, feeds are bound to individual devices - this is a requirement for easy replication, and outside the scope of this document.
A common problem is someone using a laptop + desktop or phone, and expecting to be able to have a unified identity with which to interact with
the network with.

Current clients don't have the means to support this well, and we see workaround like
- having multiple variations of your name to distinguish devices (e.g. @soapy, @soapy-laptop, @soapy-mac, @soapy-win)
- people @mentioning all the different devices an identity could be using (see e.g. above)
    - this is to make sure notifications land
    - in private messages this gets hard because there's a cap of 7 recps
- visiting multiple different profiles to see what a friend has been up to


## Requirement for a solution

Keep in mind the following are to help us focus _outward_ on the impact of whatever we design.
Let's come back to these when we're discussing possible implementations.

A good solution will 
1. Allow a great onboarding experience
    - @soapy can merge all his accounts from any device
2. Protect against unwanted merging
    - might require consent from devices being "added"
3. Allow unmerging of sameAs
    - any @soapy device can nullify the sameAs (no one-ring to rull them all)
    - TODO : does that device jsut exit, or is the whole thing void?
4. Make it easy for "@soapy" to check their notifications
5. Make it easy for "@soapy" to check their private messages
6. Make it easy for anyone to mention "@soapy" (and trust they'll get it)
7. Make it easy to DM "@soapy" and 4 other friends
8. Be easy for developers to understand (so it can be written in other languages)
9. Require a small dependency stack
10. 


(MIX: this is just my summary of what I've heard you say so far Christian, along with what's in my mind.
It will be incomplete and imperfect, I'd love to sharpen it together)


## History / Possible solutions

link out to draft solutions / summaries of experiments

- Matt's work
- Christians work
- Mix's work



