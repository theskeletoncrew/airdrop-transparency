# The Skeleton Crew
https://skeletoncrew.rip | [Twitter](https://twitter.com/skeletoncrewrip) | [Discord](https://discord.gg/skeletoncrewrip)

## Airdrop Transparency

The Skeleton Crew launched on Oct 1, at 5PM UTC. Since then, we have been sending airdrops every day, at different times, to holders of our SKULLS. The airdrop supply also changes each day, depending on the rarities of the items we want to share, and the agreements that we have with our partners and commissioned artists. This means that holding a SKULL provides you with an ***opportunity***, but not a ***guarantee*** to receive a SKULL each day.

This repo captures the receipts; the data behind our drops that details (1) what addresses identify the SKULLS in the collection (*see* `skulls-token-addresses.log`), (2) what addresses we determine to be SKULL holders - filtering out addresses of marketplace escrow accounts to the best of our ability, (3) who we randomly select as recipients of the airdrops, and (4) the logs detailing transactions in which we send SKULLS to those recipients.

## How we determine winners

At first, we were so tied up with our launch, that we didn't get a chance to complete our airdrop programming. After sending out 600+ magic 8-balls by hand through Phantom, it was time to hunker down and finish our automation. Eventually, by 10-4, we had written a suite of simple scripts to perform the workflow.

Here's the basic process of how the airdrop works each day:

1. Using a known list of ids representing each on-chain SKULL, we run a script that fetches a snapshot of all current skull holders.
2. We filter this list of holders to remove known marketplace escrow accounts (to prevent sending airdrops to the void)
3. For a given drop, we pull a list of random winners. This is basically just running the list of ids, one per line, through a random sort, and then grabbing `head -n {NUM_RECIPIENTS}`. From there the recipients are chopped into blocks based upon the sizes of the drops. ex. 1st block of 666 receive the trick of the day, 2nd block of 3 win the treat.
4. Next, we mint the trick and the treat as master editions with limited supply using the Metaplex UI.
5. With the masters in our wallet, we then run a script over each to generate all of the limited edition NFTs for that day. This takes a bit of time.
7. Now we run a script that sends each of the limited editions to the chosen recipients.
8. Finally, we head to Discord & Twitter to watch the fun that ensues :)