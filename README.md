# Okaeri SDK for Python (3.7+)

![License](https://img.shields.io/github/license/OkaeriPoland/okaeri-sdk-python)
![Total lines](https://img.shields.io/tokei/lines/github/OkaeriPoland/okaeri-sdk-python)
![Repo size](https://img.shields.io/github/repo-size/OkaeriPoland/okaeri-sdk-python)
![pypi](https://img.shields.io/pypi/v/okaeri-sdk)
![Contributors](https://img.shields.io/github/contributors/OkaeriPoland/okaeri-sdk-python)
[![Discord](https://img.shields.io/discord/589089838200913930)](https://discord.gg/hASN5eX)

Currently supported services:
- [OK! AI.Censor](#ok-aicensor)
- [OK! No.Proxy](#ok-noproxy)

Full documentation available on [wiki.okaeri.eu](https://wiki.okaeri.eu/) in:
- [Polish](https://wiki.okaeri.eu/pl/sdk/python)
- [English](https://wiki.okaeri.eu/en/sdk/python)

## Installation
```bash
pip install okaeri-sdk==1.*
```

## Example usage
### OK! AI.Censor
See full docs in: [Polish](https://wiki.okaeri.eu/pl/sdk/python#ok-aicensor), [English](https://wiki.okaeri.eu/en/sdk/python#ok-aicensor)
```python
from okaeri_sdk import AiCensor
from okaeri_sdk.client import OkaeriError
from okaeri_sdk.aicensor import AiCensorError

try:
    aicensor = AiCensor("XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX")
    prediction = aicensor.get_prediction("o cie k u r//w@!")
    swear = prediction.general.swear
    print(f"swear: {swear}")
except (OkaeriError, AiCensorError) as e:
    print(f"Error: {str(e)}")
```

### OK! No.Proxy
See full docs in: [Polish](https://wiki.okaeri.eu/pl/sdk/python#ok-noproxy), [English](https://wiki.okaeri.eu/en/sdk/python#ok-noproxy)
```python
from okaeri_sdk import NoProxy
from okaeri_sdk.client import OkaeriError
from okaeri_sdk.noproxy import NoProxyError

try:
    noproxy = NoProxy("XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX")
    info = noproxy.get_info("1.1.1.1")
    proxy = info.risks.proxy
    verify = info.suggestions.verify
    block = info.suggestions.block
    print(f"proxy: {proxy}, verify: {verify}, block: {block}")
except (OkaeriError, NoProxyError) as e:
    print(f"Error: {str(e)}")
```
