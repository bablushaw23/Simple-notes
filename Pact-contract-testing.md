# About Pact
* Ref: https://www.youtube.com/watch?v=yaAe0aR1G-U
* https://docs.pact.io/

## Before Pact
We had a part in the integration test where we spin up the required services and check if they can talk with each-other with common contract. Like in shared json template if fields are as expected.
This is a necessary part of testing as it proves that schema between publisher and consumer are common but this commonality is verbally agreed and there was no framework to enforce this at build time.
Moreover, if the contract breaks then it is client which face the trouble because their service will act wierdly whereas its publisher's fault and they should get the feedback
### Here comes Pact
Consumer first dictate the required json schema and share to a common place and publisher will fetch the shared schema and test its implementation. This test will be running over pipeline as well.
The common place is **Pact Broker**. Its will be standalone deployed service keeping records of these.

### What Pact is good for
Pact will work where both publisher and consumer will agree to use it.
- You (or your team/organisation/partner organisation) control the development of both the consumer and the provider.
- The consumer and provider are both under active development.
- The provider team can easily control the data returned in the provider's responses.
- The requirements of the consumer(s) are going to be used to drive the features of the provider.
- There is a small enough number of consumers for a given provider that the provider team can manage an individual relationship with each consumer team.

### Where Pact in not a good choice
- Testing APIs where the team maintaining the other side of the integration will not also be using Pact
- Testing APIs where the consumers cannot be individually identified (e.g. public APIs).
- Situations where you cannot control the data being used to generate the provider's responses.
- Testing providers where the consumer and provider teams do not have good communication channels.
- Functional testing of the provider - that is what the provider's own tests should do. Pact is about checking the contents and format of requests and responses and not about if the response value is valid
