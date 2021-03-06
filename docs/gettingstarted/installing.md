---
description: Learn how to install Epikcord.py!
authors: Epikcord.py
---

# Installing

## Stable Version

### :fontawesome-brands-windows: Windows

```python
py -3 -m pip install -U Epikcord.py
```

### :fontawesome-brands-apple: :fontawesome-brands-linux: MacOS/Linux

```python
# Linux/macOS
python3 -m pip install -U "Epikcord.py"
```

## Updating

```python
pip install Epikcord.py --upgrade
```

## Development Version

!!! warning
    This is not a stable version, things will work not expectedly as you thought

```python
python -m pip install -U git+https://github.com/Epikcord/Epikcord.py
```

## Repl.it

!!! warning
    Repl.it is not a good IDE. Its online, its free, but you should definitely not use it to host your bot, its not made for that purpose. Your bot will get slower as it gets bigger, and certain files might be deleted.
    
1. Create a file and name it `.replit`.
Next, you need to insert the following into the file.
``` hl_lines="3"
	language="python3"
	run = """
	pip install epikcord.py
	python yourmainfilename.py
	"""

	[packager]
	ignoredPackages=["discord.py", "discord"]
```
