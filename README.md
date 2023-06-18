<hr/>
<hr/>

<a name="readme-top"></a>

# CallOrderControl Contract

<hr/>

# Ensures your functions are only called by an address in a previously allowed order or a previously allowed number of times

## 💽Testing and implementation example repo => [(click)](https://github.com/CarlosAlegreUr/CallOrderControl-SmartContract-Testing) 💽

## 💽NPM repo => [(click)](https://www.npmjs.com/package/call-order-control-contract) 💽

<hr/>

If further elaboration or development please mention me in your work.

😉 https://github.com/CarlosAlegreUr 😉

<hr/>

## 🙀 A PROBLEM THAT SOLVES 🙀

Imagine you have a blockchain-based game where players can possess collectible items in the form of NFTs or any ERC token standard.

Now, imagine implementing a random loot box opening system using contracts like VRF from ChainLink. For each loot box, someone needs to call the VRF functions in your contract to generate a random result and then check the emitted events to retrieve the values.

However, if you allow anyone to call these functions in any order and any number of times, there is a risk of an attacker spending money to disrupt your system. They could call the function multiple times, making it more expensive to filter the contract events. Alternatively, if you restrict the VRF calls only to your team's addresses, the entire cost of opening loot boxes will fall on your business.

To reduce the cost of implementing a loot box system in your blockchain-integrated game, you can shift the burden of calling the VRF functions to the client in a controlled manner using the CallOrderControl contract. This way, your business only needs to call one function to grant permissions to the clients, which should be cheaper (although I haven't checked it yet 😅). Even if it results on not being much cheaper you still get the benefit of improved security
and control.

With this approach, you will have the ability to determine who can call which VRF function, how many times, and even in what order.

Combining this with the  [InputControl](https://www.npmjs.com/package/input-control-contract) package, you can implement a more affordable and secure method for creating a game with NFT improvements. Both the client and business can ensure that no one can modify NFT values without permission.


## 🤖 General usecase explanation 🤖

CallOrderControl can be used to control that functions are only called by an address in a previously allowed order
or a previously allowed number of times.

You can use this contract if you want the user to only call certain functions in a predefined order.
Like if you want your client to call func1, then func2 and then func3 and not in any other way. CallOrderControl
manages that.

It can also manage cases where you want just a function to be called X times regardless of the order, or even X
times taking into account the order.

<hr/>

## ✨ How to use ✨

1. Make your contract inherit CallOrderControl and add the isAllowedCall()
   modifier in the functions you desire to control. Make sure to pass the correct arguments:

   1.1 -> Function selector of the function where it's being applied:
   bytes4(keccak256(bytes("funcSignatureAsString")))

   1.2 -> msg.sender => to know who is calling.

2. Additionally you can override callAllowFuncCallsFor() if you please mixing this functionality with,
   for example, other useful ones like Owner or AccessControl contracts from [OpenZeppelin](https://docs.openzeppelin.com/contracts/4.x/access-control).

Check a simple implemented example at [UseCaseContract.sol](https://github.com/CarlosAlegreUr/CallOrderControl-SmartContract-Testing/blob/main/contracts/UseCaseContract.sol).

<hr/>

## 📰 Last Changes 📰

- Fixed bug, funcToCallsLeft mapping now is overwritten correctly. In previous version it could overflow and/or lead to unexpected behaviours.

- Added getIsSequence() function.
- Deleted argument \_isSequence ins getAllowedFuncCalls().
- New tests in tests' repository.

## 🎉 FUTURE IMPROVEMENTS 🎉

- Improve and review (static analysis, audit...) code's tests.

- Test in testnet.
- Create modifier locker. Make it more flexible and be able to activate or deactivate CallControl in your functions.
- Check gas implmications in the VRF suposed usecase.
- Check if worth it to create better option: adding more allowed calls to client who hasn't used all of them. Now it overwrites.
- Check gas implications of changing 4 bytes function selector to 32 bytes hashed function signatures.

<hr/>

<a name="realcase"></a>

## 📨 Contact 📨

Carlos Alegre Urquizú - calegreu@gmail.com

<hr/>

## ☕ Buy me a CryptoCoffee ☕

Buy me a crypto coffe in ETH, MATIC or BNB ☕🧐☕
(or tokens if you please :p )

0x2365bf29236757bcfD141Fdb5C9318183716d866

<hr/>

## 📜 License 📜

Distributed under the MIT License. See [LICENSE](https://github.com/CarlosAlegreUr/CallOrderControl-SmartContract-DesignPattern/blob/main/LICENSE) in the repository for more information.
