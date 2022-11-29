# Understanding Solidity's version Pragmas

All you need to know!

```solidity
pragma solidity >=0.7.0 <0.9.0;
```

The solidity language keeps on evolving, fixing bugs, adding features, and making semantic and syntactic changes. Some of these changes are breaking changes and might cause our contracts to not work as intended. We must specify what version of the compiler our contract will be using with version pragmas to reject compilation with unwanted compiler versions. If we don't, the compiler will issue a warning.

Solidity follows a versioning model called <a href="">Semantic versioning</a> just like <a href="">npm</a>. Semantic versioning uses the form (Major.Minor.Patch), where :

- Major - Makes no guarantees of backward compatibility
- Minor - Adds functionality in a backward-compatible way
- Patch - Used for backward compatible-bugfixes

In practice, Solidity treats the minor number as a major version and the patch number as a minor version.

You can find the list of breaking changes made, inside the Solidity documentation. Here's a link to <a href="">Solidity v0.8.0 breaking changes</a>.

### A note about <code>pragma</code>s

- The <code>pragma</code> keyword is used to enable certain compiler features and checks.
- A <code>pragma</code> directive is always local to a file.
- <code>pragma</code>s from imported files don't automatically apply to the importing file.

Most commonly, version pragmas are used as follows -

```solidity
pragma solidity ^0.8.2;
```

This indicates that the compiler should not be earlier than version 0.8.2, and not equal to or later than the next minor version (0.9.0). The caret (^) makes bugfix releases possible.

```solidity
pragma solidity 0.8.2;
```

But it's considered good practice to lock the pragma to a specific intended compiler version against which the code was tested the most, as there could be changes that could deprecate your code.

We can define more complex rules for compiler versions, we can use comparators ( =, >, <, >=, <=) they follow the same syntax as in npm.

The version pragmas don't change the compiler nor does it enable or disable features of the compiler, it just instructs the compiler to check if its version matches the one specified, if not the compiler will issue an error.
