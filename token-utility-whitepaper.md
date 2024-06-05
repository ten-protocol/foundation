# Token Utility Whitepaper - v3.0

## Introduction 
A token economy is non-trivial and continues to be an area of much research and debate in the Web3 community. This proposal document is just that, a proposal which is intended to deliver a viable starting point for a TEN token economy. The economic model is expected to evolve over the lifetime of TEN via governance proposals.

The eventual TEN implementation depends upon a network of intercommunicating TEN nodes to achieve its decentralisation, scalability and confidentiality promises. TEN node operators incur operating costs for which they need to be remunerated. This is achieved through a rewards and incentives model. TEN's native token, $TEN, provides the means for the TEN community to vote on change proposals to TEN and for ongoing development of the TEN ecosystem. The long-term TEN tokenomics have been designed to be circulatory and self-sustaining with no human intervention and no subsidies. Instead decentralised TEN smart contracts handle all token movements (transaction fees, rewards and staking).

This tokenomics whitepaper describes both the tokenomics for the bootstrapping phase of the TEN network and the long term intentions for $TEN’s utility. In summary, $TEN will have utilities after the bootstrapping phase and once the long term plans for TEN are in place. In the immediate time frame, $TEN is the means to vote on proposals for changes to TEN via a governance model.

## Bootstrapping

The eventual TEN implementation and the final outcome of this tokenomics proposal assumes a TEN network with significant traction. To get there we estimate TEN will need at least one year, most likely more. During these early days of bootstrapping we have to take into consideration ease of adoption, code maturity and security. A low friction user and developer experience has been an obsession within TEN's design underpinning many decisions.

Other major Layer 2 solutions have opted for a pragmatic approach where they have started out paying gas fees in ETH, Ethereum's native token, rather than their native token. We propose that TEN starts out similarly to these Layer 2 solutions with transaction fees and rewards being in ETH whilst the TEN token's utility remains in place as a means of providing a means of voting on proposals for changes to TEN via a governance model.

## Token Supply

$TEN is issued by the TEN Network Association, a not-for-profit association inagurated in Switzerland. The initial token supply is 1,000,000,000 $TEN. There is no minting or burning in the TEN protocol design.

## Rewards
There are three types of node rewards with TEN: a reward for being an active node and taking part in the lottery to select which node will submit a rollup; a reward for submitting a rollup to the Layer 1; a reward for making a successful challenge to an inaccurate rollup, for example transactions are missing or in the wrong order. During the bootstrapping phase rewards will be made in ETH and the reward will be limited to those nodes which are verifying the accuracy of the signed list of transaction hashes generated.

If a node finds a discrepancy with the rollup published on the Layer 1 network, it can post a challenge including the offending rollup to the Layer 1 network. The management contract will inspect this challenge. If successful during the bootstrapping phase, a reward in ETH is given to the challenging node. The value of the reward is greater than the gas cost of posting the challenge to incentivise prompt discovery of issues. Additionally the stake of the node which introduced the discrepency will be slashed with the entire stake returning to the Community Reserve.

## Token Allocation

The allocations of $TEN aim to reward ongoing participation in TEN and minimise short-termism. The largest allocations are for community members, third-party integrators and application developers building on top of TEN so they can grow and succeed alongside TEN.

| RECIPIENT             | TOKEN AMOUNT   | ALLOCATION % |
|-----------------------|----------------|--------------|
| Contributor Community | 22,500,000     | 2.25         |
| Community Reserve     | 409,500,000    | 40.95        |
| Investors             | 396,200,000    | 39.62        |
| Core Team             | 152,000,000    | 15.20        |
| Service Providers     | 19,800,000     | 1.98         |


### Contributor Community
The Contributor Community allocation is crucial for TEN to gain early traction in the wider community, achieve organic growth and for early contributors to be recognised for their efforts. It is gratifying and empowering for community members to be rewarded for being active contributors to a project as opposed to receiving the same treatment as people arriving with potentially no genuine enthusiasm for the project. It is also in the interest of the project to identify the value-adding community members and incentivise them to remain active and continue adding value to Ten over the long term.

Contributor Community tokens will be distributed to contributors from the TEN community at no cost to the contributor. Contributions are defined, captured, tracked and scored using decentralised task management tooling. The score achieved in the task management tooling indicates how much of the Contributor Community pool a contributor is entitled to. Each contributor's token allocation will be a percentage of their total contributions against the entire community contribution up to the day of TEN token launch.

The Contributor Community distribution will be conducted through a reputable third-party private offering manager so the necessary regulatory checks are completed with confidence. 

### Community Reserve
The Community Reserve exists to run and enhance TEN and develop and evolve the TEN ecosystem over time.  The TEN Network Association has oversight of how the Community Reserve is put to use. Examples include engagement with engineering talent, or protocol developers, to further develop the TEN using tokens as a form of incentive, settling of legal fees and covering other operational costs, security tests and bug bounty programs, incentivising members of the community to make meaningful contributions to TEN via incentive programs, grants, hackathons and competitions. Liquidity provisioning is also made available from the Community Reserve.

### Investors and Core Team
Providing investors and the Core Team with the opportunity to participate in the governance of TEN is an important part of their contribution to the wider TEN ecosystem. Token allocations to these groups encourage continued engagement, interest and contributions. Additionally, application builder engagement in TEN is a top priority and nurturing deep engagements with partners who can contribute to TEN in a meaningful way is vital. Encouraging investors to remain actively engaged will help open doors to high quality applications within their portfolio of companies and encourage their migration to TEN.

### Service Providers
Over the course of TEN’s lifetime there have been and will be specific expertise, talent and guidance required to make TEN a useful and successful platform. Companies that provide this service are allocated tokens to gain the opportunity to help govern TEN.

## Token Emission
Token unlocking periods have been designed to strike a balance between allowing utility from the get-go and encouraging continued high-quality development and commitment to the TEN ecosystem over a number of years.

Tokens distributed to the Contributor Community and partially unlock at TGE to allow participation in TEN as early as possible without applying downward pressure and making it difficult for others to participate through token onwership.  

Tokens distributed to the Community Reserve are unlocked on a schedule designed to provide early access to the tokens required to execute on their plans, for example, run TEN hackathons and raise awareness amongst the developer community.

Tokens distributed to Investors and the Core Team are initially locked up followed by multi-year unlocks to keep team and investor sentiment high, encourage long term focus in their investment and clearly demonstrate their commitment to the success of TEN.


### Token Unlocking Schedule

| RECIPIENT             | TGE UNLOCK % | UNLOCK CLIFF    | TOTAL VESTING PERIOD        |
|-----------------------|--------------|-----------------|-----------------------------|
| Contributor Community | 5            | 0 months        | 7 months                    |
| Community Reserve     | 1            | 0 months        | 90 months                   |
| Pre-seed investors    | 0            | 6 months        | 144 months                  |
| Seed investors        | 5            | 2 months        | 18 months                   |
| Strategic investors   | 5            | 4 months        | 24 months                   |
| Strategic2 investors  | 5            | 5 months        | 24 months                   |
| Core Team             | 0            | 7 months        | 42 months                   |
| Service Providers     | 0            | 7 months        | 42 months                   |




