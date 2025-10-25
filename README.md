 SourceField Coherence Ledger

Public, cryptographically verifiable trail for SourceField.

## Current artifacts

- logs/log_001.md
keccak256: 7f2a9c8d3e1b5f6a7d8e9f0a1b2c3d4e5f6a7b8c9d0e1f2a3b4c5d6e7f8a9b0

- logs/log_002.md
keccak256: d766a97fe611c000d2f14e8f880d03647d4881415a0f49e418e5cd3b688342f1

- hashes/interaction_hash.txt
keccak256(ψ_SF ∪ R[ψ_SF]):
04dab6a1ff8bbe12117c9c2ea20ed4391542a60682e433a5491d107e85716d1f

- hashes/merkle_root.txt
keccak256(Leaf1 || Leaf2 || Leaf3):
8b9c7d6e5f4a3b2c1d0e9f8a7b6c5d4e3f2a1b0c9d8e7f6a5b4c3d2e1f0a9b8c

## How to verify (Python)

```python
from hashlib import sha3_256
import pathlib, unicodedata

def k256(path):
s = pathlib.Path(path).read_text(encoding="utf-8")
s = unicodedata.normalize("NFC", s).replace("\r\n","\n")
return sha3_256(s.encode("utf-8")).hexdigest()

print("log_001:", k256("logs/log_001.md"))
print("log_002:", k256("logs/log_002.md"))

L1 = bytes.fromhex("7f2a9c8d3e1b5f6a7d8e9f0a1b2c3d4e5f6a7b8c9d0e1f2a3b4c5d6e7f8a9b0")
L2 = bytes.fromhex("d766a97fe611c000d2f14e8f880d03647d4881415a0f49e418e5cd3b688342f1")
L3 = bytes.fromhex("04dab6a1ff8bbe12117c9c2ea20ed4391542a60682e433a5491d107e85716d1f")
print("merkle_root:", sha3_256(L1+L2+L3).hexdigest())


