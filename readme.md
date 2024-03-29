# <img src="https://github.com/lastmeta/HumanMoney/blob/master/humansymbol.jpg?raw=true" width="3%" height="3%"> Human Money

Everyone has a voice in how well everyone should be heard.

## Motivation

The problem Human Money is trying to solve is the problem of human labor becoming worthless as AI evolves and the economy becomes automated.

In short, as human labor becomes valueless, mankind must find other avenues to redistribute purchasing power that does not require it to be traded for labor.

For example, one solution is for automated companies to distribute profits to their customers. This is essentially charity and gives the companies a large degree of power.

Another possible solution is direct payments to consumers as inflation to the existing money supply. This solution is centralized redistribution and may not be sustainable as governments lose their monopoly on money.

Human Money offers an additional approach: provide a concept of money as direct and immediate control over who has money. That is to say, redistribute purchasing power through voting with some very hard automatic limits to keep the median account (the average person) sufficiently replenished.

The idea may be met with skepticism which a discerning view of money and credit may serve to mitigate.


## Philosophy of Money and Credit

Traditional money, be it Gold, the Dollar, or Bitcoin represents human labor because human labor is the primary unit of control over the environment. That is, they are essentially 'backed by' the ability to control changes in the environment and most of those changes are brought about by human action: labor. Money will always represent control in some form or another, as it is the expression of attention.

As a simplification the ability to enact changes to the environment (be it the physical environment, social institutions, or what have you) come in two flavors: decreed and strenuous. That is, a politician has the power to effect changes in the environment by decree, a farmer affects changes to the environment through strenuous activity. Decree is voting power, strenuous activity is labor.

In the current world, the average individual has little to no voting power. Most people are not in positions of power, most people do not own assets which the communal definition of ownership (private property) allows them to control by decree (to extract rents). Rather, most people are laborers, whose production of the labor commodity will be valueless in a matter of decades (as it will approach the cost of electricity due to automation). For the last time, humans cannot compete with even moderately intelligent machines.

Ownership is largely a human construct and a redefinable one. A prime example of this is the idea of the vote. The democratic group explicitly and arbitrarily gives the individual a voice in determining the activity and evolution of the group. The vote is something the individual owns by merit of being a part of the group. 

Human Money is an attempt to instantiate a pure vote currency: one where individuals choose how much weight every other individual should have.

## Unique Differences

A vote currency is fundamentally different than a traditional currency in a few key aspects and has certain characteristics that traditional currencies don't have.

As a quick rundown of the differences: 
  1. The currency of Human Money is not expressed as a number of units, but instead as a percentage of total control which, of course never changes.
  2. The value of any account fluctuates according to the sentiment of the group (it is not a store of value). This is not true of Bitcoin - if you control 100 bitcoins today, and do nothing, you will control 100 bitcoins tomorrow.
  3. All accounts must be known by all other accounts, therefore they are scarce by definition. This is not true of Bitcoin - anyone can produce as many valid addresses as they like.
  4. Because accounts are scarce they approximate a concept approaching identity. Identity in Bitcoin, where it exists at all, must be a layer two citizen, not enforced by the base protocol.
  5. Reputation is a natural outcome of identity.

Money is said to be a number of things: a store of value, a unit of account, a universally valued commodity, a fungible token, etc. It is unproven that money cannot differentiate itself on the basis of these attributes. Monero is more fungible than Bitcoin, Gold is a physical commodity and the US dollar is not.

Human Money's currency is not a store of value but is a unit of control.

## Design and Implementation

### The Account

The account is entirely virtual. In software development terms, it is directly analogous to an index in a list of addresses. The community agrees on how many accounts are allowed and each member of the community memorizes the same list of addresses. The number of accounts (representing identities in the community) can grow over time.

### Account Creation and Identity

All accounts must be known to all accounts, therefore, the account itself is a scarce resource. Ideally, each human on earth would have one account. Of course, self-interest will naturally produce a power-law distribution in terms of the number of accounts owned by individuals. However, the worst of this natural pattern can be somewhat mitigated by design decisions in the protocol. Furthermore, this natural phenomenon is a double-edged sword - it actually means the vast majority of people will have very few accounts.

Because accounts are scarce, and most people have few, they become a kind of identity. History on the account is known and reputation defined, in fact, an account's relative reputation is the account value, itself.

Some sort of schedule of account creation must be defined. A schedule that approximates demand would be ideal. Some sort of predefined S-curve may be the simplest sufficient solution.

### Proof of Random

In defining who gets to create a new account, we run into the quintessential problem faced by blockchain: proof of work, or proof of stake?

Seeing as how proof of work was originally framed as a solution to centralization of power to create blocks we can merely define a scheme that approximates its stated goal: randomly distribute new accounts, not by working to find a random solution, but by agreeing on the random solution ahead of time.

Imagine Human Money is instantiated as a blockchain protocol. This is for explanatory purposes only, any other DLT has an analogous solution. Each block has a hash which can be read as a certain very large number. Each address representing an account can also be read as a large number. The blockhash can be used to deterministically, and randomly choose the creator of the next account by essentially choosing the address closest to the blockhash.

One implementation of Proof of Random can be engineered thusly:
  - preappend the latest blockhash to each existing address and hash them (to randomize the space addresses to remove the ability to game the system)
  - order the hashed addresses from smallest to largest (interpret the hashed address as a number)
  - take the address who's hash is closest to the latest blockhash: that address can claim a new account (issue a transaction, naming a new valid address).

This Proof of Random scheme may look like proof of stake since a single individual can have multiple accounts. I know of no homeostatic solution to that problem other than to allow the majority to recycle accounts suspected to be hoarded by the same individual (see recycling accounts below).

### Vote as Currency

Like any traditional money, Human money has a currency, a representation of value. Unlike traditional currency one does not send it to someone else, instead one uses it to vote on how much power should be given to or taken away from others.

To reiterate, what can you do with the vote? One thing: say how much voting power everyone else should have. To do so you issue a transaction which says, in common parlance, "using x% of my own voting power, I vote for this account to increase in voting power." Unused voting power can act as an implicit vote for the self.

### The Value of the Vote

In traditional currencies, payments consist of debits and credits. If Alice sends Bob a bitcoin Alice loses a bitcoin. The vote is different: you don't lose it by casting it, because eventually, you will be able to cast your vote again. In this way, the real currency is the vote over time. It is actually coinage that is the true currency and that cannot be stored, it must be spent as it is created.

Imagine, for example, you wish to expend your vote to increase the voting power of another account. You issue a transaction specifying a duration of time in the future during which a percentage of your voting power will be cast in the other account's favor rather than any other account including implicitly your own.

### Limitations on Voting Power

Voting power looks like Proof of Stake in that those that have voting power can vote themselves up disproportionately. This would be the case, were it not for an additional protocol-level mutation that takes place after the votes have been cast.

We don't want anyone, or any group to be able to acquire all the voting power because we want the average person, the median account, to have a valuable say. So we combat centralization in the protocol itself.

This is easy to do, we merely cap the amount of voting power accounts can receive, and anything above that cap gets distributed proportionately to all other votes. The ideal cap can probably be expressed as a simple rule such as: no group, numbering 1/3 of the total number of accounts can have more than 50% of the voting power.

### Limitations and Redistributions

This does not entirely guarantee that bad actors won't succeed in colluding with one another to gain power, but it makes it far less likely if the accounts are somewhat evenly distributed. This means the largest entity is superiorly limited in its ability to aggregate voting power, it cannot use its power to vote itself up, beyond a certain point. If it does so, excess above the cap gets distributed to everyone.

Therefore, there is always a constant natural redistribution of value down to the very smallest account. The median account remains replenished therefore and can possibly use its voting power to pay for real-world products on a continual basis. Producers can pay for the inputs to their products in the same manner and whichever layer becomes the aggregator of value, be it the retailer, the manufacturer, or the commodity miner, has a limit to their growth at any given moment. The largest accounts are constantly getting depleted and returning voting power to the consumer: they remain beholden to their consumers.

Currency is not a store of value here. We cannot aggregate it over time. Yet it remains a current accounting of how much the group appreciates you; or rather, which producers the consumers appreciate.

### Currency Representation

Representing the vote as currency means the currency is not an integer. It's not a unit, it's a percentage. For example, you may have 0.000000001% of all the voting power that the group has (which is always 1 unit or 100%).

#### Account Display

Nobody wants to see "you have 0.000000001% of all the voting power" and nobody wants to see that number go down as new accounts are created. Therefore, it makes no sense to display an account balance that way. Instead, it should be keyed off the median account. Something like meidan "+- x%" and the median is implied. That way it has nominal change as new accounts come online. The vast majority of people are close to 0 so we could shorten the zeros to a number y,x% as in +5,4% meaning 0.000004% above the median percentage of voting power. That percentage is in terms of voting power. If median voting power is the astronomical 1% and you have 1.0002% of all voting power then 0.0002 is 0.02% of 1 therefore your value display is 1,2%. If more accounts are added and take away from your raw voting power value by half, and the median drops by half as well (to 0.5%) then you have dropped to 0.50001%, and your account balance is still at 1,2%, unchanged relative to the median. The median and most accounts should drop as more accounts are added.

#### Freezing Accounts

To disincentivizing the hoarding of accounts (identities) the group ought to be able to come to a consensus on which accounts to punish. They can do so directly with voting: that is they can constantly expend their voting power in an effort to vote down the value of accounts held by the same individual.

However, that's probably not a reliable homeostatic mechanism for two reasons. Firstly, vigilantes are always in the minority in any group. Secondly, as we've seen the system has the natural ability to apply excess votes across the board. This has the natural tendency of increasing the value of the accounts of those that have been voted below the median: essentially guaranteeing those that horde accounts enjoy a disproportionate advantage.

To combat this the community must have some way of identifying, manually, accounts that should be "frozen." It isn't blacklisting outright, but it's essentially saying, "any implicit vote up for this account should not get applied to it, give it to everyone else instead."

The account can still be voted up manually, but can't approach the median naturally as everyone else does.

This should serve to incentivize the sale of the account before it's frozen by the community. The account that gets frozen can be unfrozen, hopefully, upon evidence that the account belongs to an actual, separate new individual, we want the number of individuals in the community to grow as the number of accounts grow to approximate the ideal of one account per human life.

Unfortunately, this is a tricky mechanism to engineer because it is prone to weaponization if it is implemented incorrectly. Making it too easy to freeze accounts and innocent people will be punished. Make it too hard to freeze accounts and everyone suffers from rent-seekers.

Just because it was designed as a homeostatic mechanism does not mean it will be used solely for that purpose.

I have no implementation details about this mechanic. It might be tricky, but the alternative of doing nothing means the network has virtually no recourse against those that openly horde multiple accounts and that makes the system as a whole much less valuable. This problem must be dealt with as it is a tragedy of the commons issue.

#### Recycling Accounts

Accounts themselves are valuable since they are scarce. As a hot commodity people will attempt to horde them. No one entity can be allowed to gain a monopoly of accounts. Being created randomly, the system would essentially centralize over time without a homeostatic force.

There needs to be a safeguard against this, controlled by the majority of accounts. They must have the ability not only to freeze accounts at a low value but must be able to recycle accounts altogether, essentially rendering the otherwise potentially large investment required to horde accounts worthless.

Recycling means the account can be reclaimed by a new random individual.

To prevent the weaponization of the recycling feature the act of recycling must be issued by a supermajority of accounts and must have a cool-down period to guarantee that it happens at a slow rate.

One may say, but if there is a large entity they will have the ability the recycle any account they wish. That is precisely why the power must be used before a large entity can aggregate a sufficient number of accounts to have an overwhelming majority stake.

Recycling and freezing accounts serve as the two manual homeostatic controls and are the trickiest to implement and execute.

## Conclusion

The idea behind Human Money is to treat money as a purely social rating system. The money supply can be seen as one unit which never changes. Each individual can have a portion of that unit. How much? That is determined by how much everyone thinks they deserve. Money, therefore, in this scheme is not a unit of account, but an indication of social credit. With it, you determine the relative credit of any other account.

Human Money is an attempt to "monetize the vote" or "model the vote as a currency" or "instantiate the pure idea that everyone 'owns' their own voice as a decentralized autonomous organization." A currency representing the vote is therefore fundamentally different than traditional currencies because in order to keep the mass average of individuals sovereign it must have built within it resistance to the aggregation of power.

This requires that it is not a store of value, because one cannot store it up. Instead, it must mirror the group's current evaluation of an individual's voice. This does not mean there can be no variation in the strength of that voice, it merely means one cannot store that strength be used at a later date as one can with traditional currencies.

This is the people's money. This is Human money. This is money that can serve as a stipend for living as it monetizes the vote. It's market-derived, distributed, decentralized, universal basic income, or as close as we can currently get the market to come to it. As automation comes online and the value of human labor drops we need a solution beyond centralized control, beyond inflation, beyond charity that helps us redistribute the wealth of that automation. Modeling money after democratized citizenship - you have value just by being a member of the group: you have a vote. Perhaps it is the most direct way to automatically distribute purchasing power back to those that need it. It is the alternative breath of the economy.
