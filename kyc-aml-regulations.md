# Product Requirements (PRD) - AML & Sanctions Compliance

This document explores the requirements around the Anti-money laundering (AML), Know-your-customer (KYC) and Sanctions laws in the US and UK jurisdictions as they apply to Obscuro.

The focus is on the UK and the US as Obscuro has citizens of the United States and the United Kingom, and is incorporated in the United Kingdom. As such, we are likely to be held to both jurisdictions laws and rules. For the UK, Obscuro is registered in the UK and is therefore subject to UK laws. While we do not operate in the U.S., American citizens (or any exposure to American citizens) require adherance to U.S. laws. OFAC calls this out specifically:

> "Once a U.S. person determines that they hold virtual currency that is required to be blocked pursuant to OFAC’s regulations, the U.S. person must deny all parties access to that virtual currency, ensure that they comply with OFAC regulations related to the holding and reporting of blocked assets, and implement controls that align with a risk-based approach."

These compliance regulations collectively form a set of rules that are largely targeted toward money transmitters, but also trade activities, with the purpose of ensuring criminal activity is captured, blocked and assets frozen. It is not simply a set of U.S.laws. It is a set of laws that span 34 countries which align to the guidance of the Financial Action Task Force on Money Laundering (FATF) based in Paris.

While it is unlikely we'll attract the attention of regulators in our early stages we want to be prepared for the success we hope for and ensure that we are able to operate a platform that is both compliant to regulation across the countries Obscuro operates and does not facilitate illicit activities. Our current proposed solution of a one year revelation period is likely insufficient for this purpose. Additionally, our privacy capabilities are specifically on the list of services that are under scrutiny by U.S. agencies such as the treasury which calls this out as a risk in the National Money Laundering Risk Assessment.

This document is broken into the following sections:

1. Summary of findings
3. Requirements - AML & KYC
2. Requirements - Sanctions
3. Money trasmitter classification

## Summary of findings

Three functional areas stand out as potential risks and opportunities:
1. Native transfer
2. The encrypted ledgers ability to support law enforcement investigations
3. General perception of crypto among general population and institutions

As we are implementing Ethereum's native transfer capability at the platform level we are at risk of being viewed as a money transmitter and would be subject to all the related laws and requirements for money transmission. Precedent appears to have been set with certain Ethereum contracts, as well as Bitcoin, being viewed as money transmitters.

If we indeed fall into a category viewed as a money transmitter, due to this capability, we would need to put in place controls for movement of cryto tokens to ensure we capture the KYC details of the users, follow AML rules on transactions and put in place controls to block sanctioned entities or individuals and seize assets. This includes reporting requirements for transactions within ten days. If we chose to not implement the native transfer capability we hamper capabilities of the platform and don't hold up our promise of matching Ethereum APIs.

Regulations require the ability to support law enforcement agencies in their investigations related to criminal activities potentially occuring on the platform. Our reveal period of a year is an arbitrary timeframe and is unlikely to satisfy this general requirement as AML requirements are to block transactions as they occour and reporting must be done within a ten day period. 

However, viewing the ledger as only two transaction types, native transfer and contracts, allows us to separate the requirements. If we chose to retain native transfer capabilities we could greater satisfy this requirement by having an immediate reveal period for transfers. This ensures we are not blocking investigations (but does not satisfy AML requirements). We can better satisfy contracts in a number of ways, but primarily through a set of contracts that platform contracts can use for compliance. These contracts would enable reporting, monitor transactions that may meet AML criteria among other capabilities.

The increased scrutiny by regulators is changing the perception of crypto by general users. Regardless of our views we have to interact with other entities that are regulated, such as exchanges. FTX blocking Aztec transactions is a good example of the impact of this. To increase adoption, and differentiate the platform, we have an opportunity to position Obscuro as the platform where the user base of institutions is able to trade and remain compliant. The AML contracts noted above are a good exmaple of how users and institutions can gain confidence while ensuring these complex requirements are met in a consistent, simple way by other contracts. Additional capabilites such as DAO voting on what contracts can deploy or requirements for KYC of contract issuers adds additional gurantees of compliance.

Recommendations:
- Determine if native transfer capabiilies position us as a money transmitter via the guidance of legal counsel.
- Determine the impact of removing the native transfer capability. This requires an analysis of contracts in production on Ethereum today. If not critical then recommendation is to remove the direct transfer capability. Evaluate this option with legal counsel advice.
- Investigate, and implement, additional capabilities to enhance the platforms ability to eanble contracts to adhere to relevant laws. This is explored later in this document but requires further research.

The remainder of this document is an exploration of specific requirements we need to address in the platform.

# Requirements - Anti-money Laundering (AML) & Know-your-customer (KYC)

AML requirements are established by the Financial Action Task Force on Money Laundering (FATF) based in Paris. They are an outcome of many decades of legislation in the U.S. but primarily from the most recent legislations following 9-11 to prevent financing of terrorist organizations. The guidance is established by the FATF and implemented by local agencies in the paticipating FATF countries.

KYC rules are a subset of the AML rules that require any financial institution (or trading company) to ensure their customers are not sanctioned or for organizations do not contain ultimate beneficial owners that are sanctioned.

U.S. AML legislation and priorities are established based on the guidance of the annual money laundering risk assessment. The FATF generally follows the guidance of the U.S. legislation as the U.S. requires AML enforcement for all entities that wish to have access to the U.S. banking system.

Crypto and blockchain platforms are identified specifically in this analysis under various names such as 'virtual assets'. The guidance is such that most agencies regard regulation already being applied to crypto, in contrast to the often held view that regulation is forthcoming. This is due to the classification of many crypto contracts and platforms as money service providers. Privacy platforms, or contracts, similar to Obscuro are called out specifically. They are referred to as "Anonymity-Enhanced Cryptocurrencies and Service Providers" and are identified as a specific risk.

> "In the United States, digital assets is a broad term that includes so-called digital currencies, stablecoins, and other terms used in the industry. Depending on the circumstances, digital assets can be securities, commodities, derivatives, or something else. Public information on investigations ofen uses the terms virtual currency or cryptocurrency. This report uses the terms virtual asset and VASP, terms not contained explicitly in U.S. law or regulation,to align with the terminology defined by the FATF."

Again in the [2020 review of Switzerland](https://www.fatf-gafi.org/media/fatf/documents/reports/fur/Follow-Up-Report-Switzerland-2020.pdf) they call out regulation 15 (from 2012) noting blockchain must meet the same requirements of any financial institution.

> "VASPs are required to comply with the requirements of Recommendations 10 to 21, to the same extent as other financial intermediaries."

The use of a DAO is unlikely to shield Obscuro Labs from being implicated in any actions. This is called out specifically in the money laundering risk assessment.

> "While some DeFi services purport to run autonomously without the support of a central company, group, or person, many have a controlling organization—through a decentralized autonomous organization, concentrated ownership or governance rights, or otherwise—which provides a measure of centralized administration or governance."

## National (US) Money Laundering Risk Assesment

The Department of the Treasury conducts an annual assesment of money laundering risks, published [here](https://home.treasury.gov/system/files/136/2022-National-Money-Laundering-Risk-Assessment.pdf). Notably, in 2022 they have identified 'virtual assets' as a risk category. 

> "When VASPs (virtual asset service providers) fail to register as MSBs (money services businesses) with FinCEN or do not implement suficient AML controls, such as filing SARs or keeping certain records, criminals are more likely to exploit those VASPs without detection. Businesses that provide virtual asset services that are required to, but fail to, register with federal functional regulators such as the CFTC or SEC create similar vulnerabilities. "

It is clear they view virtual asset providers (a category we'd likely be consider a member of) as responsible for compliance on all AML related laws:

> "Members of the virtual asset industry are responsible for ensuring that they do not engage, directly or indirectly, in transactions prohibited by OFAC sanctions, such as dealings with blocked persons or property, or engage in prohibited trade- or investment-related transactions. All companies in the virtual asset industry are encouraged to develop, implement, and routinely update a tailored, risk-based sanctions compliance program. OFAC has authority to impose civil penalties for failures to adhere to OFAC sanctions requirements. The brochure complements OFAC’s frequently asked questions on virtual currency as well as its updated advisory highlighting the sanctions risk associated with ransomware payments and “mitigating factors” in any related enforcement action."

## Product Requirements - KYC

KYC, know your customer, is a set of regulatory principles laid out by the FATF with the purpose of ensuring terrorist and other illicit players are unable to use the American banking system for illicit purposes. They are more formally known as 'customer due diligence' guidelines. It is a subset of the AML preventative measures. KYC guidelines are set out in the FATF [recommendations](https://www.fatf-gafi.org/media/fatf/documents/recommendations/pdfs/FATF%20Recommendations%202012.pdf) from 2012. 

As the recommendations are written in 2012 they predate much of the public blockchain infrastructure. However, the guidance from OFAC provides clarity in how the AML laws apply to blockchain platforms. The recommendations have the following basic requirements:

- Customer due diligence. The process of knowing your customer. This includes identifying the customer, identifying the beneficial owner (the ability to see through organizations designed to obsfucate the ultimate beneficiary) and ongoing due diligence. Companies may achieve the CDD requirements through a third party but retain the liability.
- Record keeping. A requirement on keeping records for five years that may be demanded by local agencies in investigations including transactions and documents from CDD.
- Politically exposed persons identification. Comparison of customers in KYC, and parties to a transaction in AML, against the sanctions list discussed below.
- Reporting of suspicious transactions. Compliance with the sanctions reporting requirements discussed below.

# Requirements - Sanctions

In the wake of the Tornado Cash [sanctions](https://home.treasury.gov/news/press-releases/jy0916) it is clear that we need to understand the basic requirements that may potentially be imposed on Obscuro both as an organization and network. This is the second sanctioning of a blockchain based mixer following blender.io's [sanctioning](https://home.treasury.gov/news/press-releases/jy0768) in May of 2022. OFAC (Office of foreign assets control) is the department within the U.S. Treasury tresponsible which:

> "administers and enforces economic and trade sanctions based on US foreign policy and national security goals against targeted foreign countries and regimes, terrorists, international narcotics traffickers, those engaged in activities related to the proliferation of weapons of mass destruction, and other threats to the national security, foreign policy or economy of the United​ States."

Sanction programs include:
1. broad based sanctions or embargoes (ex: North Korea)
2. government or regime sanctions
3. list based sanctions (listed persons or entities)
4. sector based (ex: arms to specific countries)

The specific individuals, entities etc are all listed in two documents in various data formats: the SDN list & the Consolidated Sanctions List. Per the FATF recommendations it is the responsibility of financial and trade related organizations to implement proper controls for enforcing sanctions.

Organizations that are under the jurisdiction of OFAC are required to ensure they adhere KYC & AML laws in place in the 34 countries that adhere to the guidance of the Financial Action Task Force on Money Laundering (FATF). A key part of the AML laws are ensuring entities and individuals in sanctioned countries, industries or appearing on a list of sanctioned individuals are not party to any transactions and prevented from using financial services. Maintenance and enforcement of these lists are the responsibility of OFAC.

Note the sanctions laws are 'strict liability' meaning 'U.S. persons may be held civilly liable for sanctions violations even without having knowledge or reason to know it was engaging in such a violation'. Additionally they note, 'Delaying development and implementation of a sanctions compliance program can expose virtual currency companies to a wide variety of potential sanctions risks. It is never too soon to evaluate potential sanctions risks; this includes virtual currency companies that are in the beta testing stage of their operations. Such companies should consider sanctions compliance during the testing and review process so that sanctions compliance can be accounted for as technologies are being developed and prior to launching a new product'.

## UK specific sanctions laws

"HM Treasury implements and enforces [financial sanctions](https://www.gov.uk/guidance/uk-sanctions), through its Office of Financial Sanctions Implementation (OFSI)". Sanctions are enforced by the [Sanctions and Anti-Money Laundering Act 2018](https://www.legislation.gov.uk/ukpga/2018/13/contents/enacted).

Crypto is clearly noted as falling into the financial sanction guidance per the "General guidance for financial sanctions under the Sanctions and Anti-Money Laundering Act 2018" (see PDF).

> "Crypto assets – Statutory definitions of “funds” and “economic resources” are wide, as referenced above.Crypto assets are considered to be covered by these definitions and are therefore caught by the financial sanctions restrictions."

The UK sanctions laws, and responsibilities, appear to be largely the [same](https://www.legislation.gov.uk/ukpga/2018/13/section/3/enacted) as the US, as discussed below.

## Transaction monitoring

U.S. persons are required to reject transactions and in many cases seize block property if the property meets the criteria of the sanctions. They must report this within 10 days in most scenarios. Reported activities include:
- blocked property reports
- rejected transaction reports

"Additionally, in most sanctions programs, any transaction that causes a violation — including a transaction by a non-U.S. person that causes a U.S. person to violate sanctions — is also prohibited. For certain sanctions programs, U.S. persons, wherever located, also are prohibited from facilitating actions on behalf of non-U.S. persons if the activity would be prohibited by sanctions regulations if directly performed by a U.S. person or within the United States. U.S. persons are prohibited from engaging in transactions with SDNs or blocked persons, directly or indirectly, and must block any property in their possession or control in which an SDN or a blocked person has an interest."

Crypto is specifically called out in transaction monitoring:

> "Once a U.S. person determines that they hold virtual currency that is required to be blocked pursuant to OFAC’s regulations, the U.S. person must deny all parties access to that virtual currency, ensure that they comply with OFAC regulations related to the holding and reporting of blocked assets, and implement controls that align with a risk-based approach."

> "Blocked virtual currency must be reported to OFAC within 10 business days, and thereafter on an annual basis, so long as the virtual currency remains blocked."

## OFAC specific 'virtual currency' guidance

OFAC has laid out specific [guidelines](https://home.treasury.gov/system/files/126/virtual_currency_guidance_brochure.pdf) for 'virtual currency' platforms. From this document the guidance states that the virtual currency industry must comply with the AML laws. In particular it calls out "Anonymity-Enhanced Cryptocurrencies and Service Providers" on page 49 which specifically addresses privacy platforms and notes that they are often used for criminal purposes.

> "Those in the virtual currency industry play a critical role in complying with their Anti-Money Laundering/Countering the Financing of Terrorism (AML/CFT) and sanctions obligations to prevent sanctioned persons and other illicit actors from exploiting virtual currency to undermine U.S foreign policy and national security interests. As part of that effort, the industry should take a risk-based approach to assess the risk associated with different virtual currency services, implement measures to mitigate risks, and address the challenges anonymizing features can present to compliance with AML/CFT obligations."

- Requirement to block users from sanctioned countries. In two case studies they note the need to validate information on users including provided KYC data as well as 'Virtual currency companies with strong sanctions compliance programs should be able to use geolocation tools to identify and prevent IP addresses that originate in sanctioned jurisdictions from accessing a company’s website and services'. They go further noting the need for catching those circumventing IPs: 'Analytic tools can identify IP misattribution, for example, by screening IP addresses against known virtual private network (VPN) IP addresses and identifying improbable logins (such as the same user logging in with an IP address in the United States, and then shortly after with an IP address in Japan)'.

- Requirement to block users with specific addresses on the SDN list. "In 2018, OFAC began including certain known virtual currency addresses as identifying information for persons listed on the SDN List.". This is complicated by a requirement to check for related addresses "A lookback could also identify connections to unlisted addresses that have previously transacted with the listed address, as such unlisted addresses could also pose sanctions risk depending on the nature of those transactions."

# Money Transmitter classification

The national money laundering risk assessement has guidance on what counts as a 'money transmitter' as it relates to crypto.

> "Some virtual assets allow instantaneous transactions without the involvement of a financial institution with AML/CFT obligations. These transactions may also be transferred across jurisdictional boundaries and may be anonymous. VASPs doing business wholly or in substantial part in the United States qualify as money transmitters, which means they are required to comply with the BSA obligations that apply to MSBs, including registering with FinCEN; developing, implementing, and maintaining an efective AML program; filing SARs and currency transaction reports (CTRs); appointing a chief compliance oficer; conducting training; and maintaining certain records. When operators of these VASPs violate the BSA or neglect regulatory requirements, such as failing to establish efective AML programs or report suspicious activities, their actions present a vulnerability to the financial system."
 
Fincen defined 'Coin Ninja' as “money transmitters” as defined at 31 C.F.R § 1010.100(ff)(5) and a “financial institutions” as defined at 31 C.F.R § 1010.100(t). It [fined](https://www.fincen.gov/sites/default/files/enforcement_action/2020-10-19/HarmonHelix%20Assessment%20and%20SoF_508_101920.pdf) the CEO $60m  for conspiracy to launder monetary instruments and the operation of an unlicensed money transmitting business. Exchangers of convertible virtual currency are “money transmitters” and “financial institutions” by Fincen's definition. Notably, each trasmission was considered a violation and the fine was $8,457 per transmission. It seems that the target of Coin Ninja, and more recently Tornado Cash, were based on the activity of money laundering not simply a lack of compliance.

> "Mr. Harmon, doing business as Helix, willfully (a) failed to register as a money services business;7 (b) failed to implement and maintain an effective anti-money laundering (AML) program; 8 and (c) failed to report certain suspicious activity. In addition, FinCEN has determined that on or about July 13, 2017 through December 3, 2019, Mr. Harmon willfully participated in Coin Ninja’s failure to register as a money services business."

However, the treasury language leaves some uncertainty for unhosted wallets which should be explored with legal counsel:

> "Users of unhosted wallets can retain custody and transfer their virtual assets without the involvement of a regulated financial institution, and these unhosted wallet transfers of virtual assets are ofen referred to as P2P transactions. Because unhosted wallet users can transact without involving any financial services provider, many of the most important obligations of the U.S. AML/CFT regime applicable to financial institutions may not apply."

Our intention is to establish a foundation in Switzerland. This is largely with a view that operating there is an environment where regulation is more progressive in regards to blockchain. The [2020 FATF review of Switzerland](https://www.fatf-gafi.org/media/fatf/documents/reports/fur/Follow-Up-Report-Switzerland-2020.pdf) 'recommendation 15' has specific language for Switzerland and a summary of the current view in Switzerland.

> "VASPs are required to comply with the requirements of Recommendations 10 to 21, to the same extent as other financial intermediaries."... "Therefore, in line with the applicable requirements of Recommendations 26 and 27, VASPs are supervised by financial supervisors which are either the FINMA or the Swiss OAR."

It also calls out an earlier recommendation to countries (recommendation 15) that seems to give it claim to jurisdiction over crypto.

> "address obligations related to virtual assets (VA) and virtual asset service providers (VASPs). These new requirements include: requirements on identifying, assessing and understanding ML/TF risk associated with VA activities or operations of VASPs; requirements for VASPs to be licensed or registered; requirements for countries to apply adequate risk-based AML/CFT supervision (including sanctions) to VASPs and that such supervision should be conducted by a competent authority; as well as requirements to apply measures related to preventive measures and international co-operation to VASPs."

# Exploration of possible ways to meet more stringent requirements

- DAO voting of Dapps to ensure Dapps that migrate to the network are known
- Requirement to KYC Dapp publishers
- KYC of end users
- Provide a set of contracts that allow Dapps to remain compliant