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
