# Programmable Inscriptions BRC-555 Research

## Goal
Test minting a BRC-555 programmable inscription.

### Examples:
- [Example 1](https://x.com/ExtraordinalBTC/status/1804290103738585329)
- [Example 2](https://magiceden.io/ordinals/item-details/7a9a199c20cca6dd05f32e3aec6fc9908a849a0fde87c7a9c2e0413a17b2759ai990)
- [Example 3](https://magiceden.us/ordinals/marketplace/xounchained)

### Resources:
- [BRC-555 Programmable Ordinal Standard](https://extraordinalsbtc.gitbook.io/brc-555-programmable-ordinal-standard)
- [GitHub Repository](https://github.com/Extraordinals/BRC555)

### Why would we want to do this:
From our resource:
> “BRC-555 is a new standard enabling programmability for ordinal collections. It allows individual inscriptions and/or complete ordinal collections to be modified based on a comprehensive infrastructure of parent-child relationships. Its modular structure enables the division of inscriptions into as many parts as desired, thus facilitating efficient updates at a lower cost.”

## Testing Steps
Generally following this [GitHub guide](https://github.com/Extraordinals/BRC555).

### 1. Inscribe the root parent
- This can be anything but will represent the collection forever, so choose something meaningful (e.g., a company logo).
- The root parent needs to be kept safe because we can inscribe new composite parents based on it.
- Completed using ordinalsbot and a skunkworks logo: [Transaction](https://mempool.space/tx/8fc1958a0349d23dcd0c09f34de15b12d8028d93b4f5348fcd000b83bedbfc9c).
- [Inscription](https://ordiscan.com/inscription/75896704).
- Inscription ID: `dbd7f294b59f8ad1d34face1aee2b8175f3e2e0639805612fa465dc0b595e787i0`.

### 2. Inscribe a child to the root parent (the "layered parent")
- Inscribed a text file as a child to the inscription above.
- [Transaction](https://mempool.space/es/tx/25aa73d47bf513e8e3ab12c51d7579646815076ad2508eceb4c084649da8b4a3).
- [Layered Parent Inscription](https://ordiscan.com/inscription/75900891).

### 3. Inscribe the `inscription.js` file
- **Question on Step 3:**
  - Does `fetcherID` stay constant, or do I need to change it with my own inscription?
  - `const fetcherId = "/content/e79ea5aa40fd255406f44cf508d18e853cb982fd0f2734c98cd008934088cd4di0";`
  - **Answer:** It is constant; you don't need to reinscribe.
- [Transaction](https://mempool.space/tx/9dc52c1eaf139b2287a73eadcc2b554542b94dbf9e9fe08ce1e072019caa2c67).
- [Inscription](https://ordiscan.com/inscription/75923130).

### 4. Inscribe the `inscription.html` file
- Replace the ID here:
  ```html
  <script src="/content/YOUR-INSCRIPTION-JS-ID"></script>
  <script src="/content/e95966181d7300bd6431ff7bc210b3878e448d51fbce59ef0a6adabff6380609i0"></script>
- [Transaction](https://mempool.space/tx/898303fce4167c1a2641fda31f8d7d71f31b069ccde3f0a9e1cb26cc141b3d31).
- [Inscription](https://ordiscan.com/inscription/75923596).
Question I had on this step:
"Inscribe the inscription.html File:" 
Is this supposed to be a child of any of the previous inscriptions or is it just stand alone?

Answer: just stand alone, it contains only inscription.js id

### 5. Inscribe `initialize.js`, `loader.js`, and `style.css` files
Note that these don’t really need any customization except for filling in the inscription IDs where needed.

- **Background Image:**
  - [Inscription](https://ordiscan.com/inscription/75923732).

- **`initialize.js` Inscription:**
  - [Transaction](https://mempool.space/tx/f29a1b7e0508505c6a539393e8f0fc2b703c994d8e7d5fddd5258a2c99288703).
  - [Inscription](https://ordiscan.com/inscription/76009496).
  - ID: `51b2ab08b5a34e416e9aa90000f50e4c036562e3a88595ac9efd3b66de8d18c6i0`.

- **`loader.js` Inscription:**
  - [Transaction](https://mempool.space/tx/aca2d2a3666ca14715d89ad134a8a5e4a71a508cb31cae2dba5f40f41c8f2f3b).
  - [Inscription](https://ordiscan.com/inscription/76009495).

- **`style.css` Inscription:**
  - [Transaction](https://mempool.space/tx/26c8adf36dafa4f4ffc3aa8289a9646a0d24e3ab629e765c0ae7295e005bd0a7).
  - [Inscription](https://ordiscan.com/inscription/76009762).

**Question:** Any customizations for `initialize.js` or `loader.js`?
- **Answer:** No customization needed; changes will be in the library.

### 6. Inscribe the `library.json` File as a child of the layered parent
- [Transaction](https://mempool.space/es/tx/40873c27d060bb9b324512bf4d7fab4cc76c4ae165e7b8f447f1e50028327255).
- [Inscription](https://ordiscan.com/inscription/76010202).

### This should be the infra complete - next step TBD
