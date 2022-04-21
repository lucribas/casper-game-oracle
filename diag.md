
#### 2.1. Best practices

| CRITERIA | MEETS SPECIFICATIONS | Status |
|:-------:|:-------|:--------|
| Smart Contract Separation | Smart Contract code is separated into multiple contracts:<br> 1) VRFData.sol for data persistence <br> 2) VRFApp.sol for app logic and oracles code |  |
| Operational status control is implemented in contracts | Implemented operational status control. |  |
| Fail Fast Contract | Contract functions “fail fast” by having a majority of “require()” calls at the beginning of function body |  |

#### 2.2 Providers

| CRITERIA | MEETS SPECIFICATIONS | Status |
|:-------:|:-------|:--------|
| Provider Contract Initialization | First provider is registered when contract is deployed. |  |
| Multiparty Consensus | Only existing provider may register a new provider until there are at least four providers registered* |  |
| Multiparty Consensus | Registration of fifth and subsequent providers requires multi-party consensus of 50% of registered providers* |  |
| Provider Deposit Guarantee | Provider can be registered, but does not participate in contract until it submits funding of 10 ether |  |

A number is not random by itself, because it is the process that generated the number which leads to the conclusion that the number is really random. Thus, to generate a really random number is necessary to:
- Use a pseudo random number generator, preferably a cryptographically secure PRNG.
- Have multiple entropy sources to build the final result. Is important to note that we need at least two actors; the user and the entropy provider(s).
- None of them should be influenced by the actions of the rest of the parties in the process.



1. Game contract asks for a random number and pay a tax for  it.
2. 


```plantuml
scale 350 width
[*] --> NotShooting

state NotShooting {
  [*] --> Idle
  Idle --> Configuring : EvConfig
  Configuring --> Idle : EvConfig
}

state Configuring {
  [*] --> NewValueSelection
  NewValueSelection --> NewValuePreview : EvNewValue
  NewValuePreview --> NewValueSelection : EvNewValueRejected
  NewValuePreview --> NewValueSelection : EvNewValueSaved

  state NewValuePreview {
     State1 -> State2
  }

}
@enduml
```

