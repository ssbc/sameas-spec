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

1. Allow a great onboarding experience
    - @soapy can merge all his accounts from any device

2. Protect against unwanted merging
    - might require consent from devices being "added"

3. Allow unmerging of sameAs
    - any @soapy device can nullify the sameAs (no one-ring to rull them all)
    - TODO : does that device just exit, or is the whole thing void?

4. Notifications
    - anyone should be able to mention "@soapy" easily
    - "@soapy" should be able to check their notifications

5. Private messages
    - private messages should be accessible from any part of the identity
    - one identifier per "identity" so we don't blow the recps cap

6. Can be implemented in multiple languages
    - relatively easy to understand
    - small dependency stack


## History / Possible solutions

link out to draft solutions / summaries of experiments

- Matt's work
- Christians work
- Mix's work

## Questions

**A. Unique id**
- mix: I think we should have a unique ID for a identity. What should it be though?
    1. any one of the feedIds in in the identity? (then lookup the sameAs and infer the others)
        - problem: what happens when the sameAs changes over time? e.g. a cypherlink says @mix, but then one device peels out from that ... when you click the link later what do you get?
        - problem: what do you do with recps then, use all the feedIds (NO)
    2. a concat of all the feedIds currently in sameAs
        - it's explicit!
        - problem: what to do with recps?
    3. a unique id associated with the sameAs / identity record which binds the identities
        - can use the history of edits on this record to answer questions about "who was in the identity when"
        - can attach a public key to this identity for DMs
            - should not use that for id, as might want to cycle it
        - problem: how to use this id as an 'author' in ssb-crut-authors ?
            - identity needs a concept of sequence, and a multi-feed identity has no absolute order..
        - Could address requirements (2) (3) using ssb-crut-authors
            - adding another feed as an author to an identity records is inviting them
            - they can then edit a consent field (and we consider only edits from a feed adding itself to that field as valid)
            - any identity could remove the authorship of another one to kick it (so sameAs = author + consent)

**B. Tangle?**
- mix: Do we tangle together the messages published by the feeds in an identity?
    - i.e. each message has `content.tangles.identity = { root, previous }`
    - this would allow quick lookup of messages by a particular "identity" (requirement 4)
    - would offer some _partial_ ordering, which might be needed for permissoins on e.g. record authorship (though is this enough?)

**C. Signing**
- mix: if we have a unique identity record which we can attach DM + signing keys to, then all messages could be signed by the identity
    - might not be necessary

    


