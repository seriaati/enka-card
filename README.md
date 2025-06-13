#  Enka.Network Card Generation (Python-Based)

<img src="https://i.imgur.com/wep9hgK.png" width="100%"><br>

## About

A python-based card generation script that allows users to generate Enka.Network cards with ease.

## Project Stack

- [EnkaNetwork.py](https://github.com/mrwan200/EnkaNetwork.py) - Enka.Network API Wrapper
- [Pillow](https://github.com/python-pillow/Pillow) - Python Imaging Library

## Initial Setup

Install the required dependencies:

```shell
pip install -r requirements.txt
```

## Usage
Change the UID in `main.py` to your UID.
```python
import asyncio

from enkanetwork import EnkaNetworkAPI, Language
from generator import generate_image

client = EnkaNetworkAPI(lang=Language.EN) # <- Change to whichever language you want
uid = 604905943 # <- Change this to your UID

async def main():
    async with client:
        data = await client.fetch_user(uid)
        for character in data.characters:
            print(f"[{uid}] Generating enka-card for {character.name}")
            generate_image(data, character, client.lang)

asyncio.run(main())
```

Run the script:
```shell
python main.py
```



Your character cards will be output in the `/output` directory. Happy generating!
