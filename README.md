# Pygame-BitmapFont

A lightweight and easy-to-use library for rendering bitmap fonts in Pygame.

![extractor.png](demo.png "Extractor tool")

## Overview

Pygame-BitmapFont provides a simple way to load and render text using pre-rendered bitmap font images and associated font data files. This approach is often preferred in game development for its performance and consistent look across different platforms.

**Key Features:**

* **Easy Integration:** Designed specifically for Pygame, ensuring smooth integration into your game projects.
* **Multiple Font Formats:** Supports custom `.json` human-readable and editable font formats.
* **Efficient Rendering:** Leverages Pygame's `Surface` and drawing capabilities for fast text rendering.
* **Customizable:** Offers options for color, scaling and text alignment.
* **Clear Examples:** Comes with illustrative examples to get you started quickly.
* **Tools Included:** Comes with CLI `bitmapfont-extract` tool for easy preparation of `.json` fonts from bitmap images.
* **Installable via pip:** Easily install the library using the Python package installer.

## Installation

1.  **Prerequisites:** Make sure you have Pygame installed in your Python environment. If not, you can install it using pip:
    ```bash
    pip install pygame
    ```
2.  **Install via pip (Recommended):** Once the package is available on PyPI, you can install BitmapFont using:
    ```bash
    pip install git+https://github.com/xdoko01/Pygame-BitmapFont.git
    ```
    or
    ```bash
    pip install pgbitmapfont
    ```
3.  **Alternatively (for development or if not on PyPI):**
    * **Download or Clone:** Clone the entire repository:
        ```bash
        git clone [https://github.com/xdoko01/Pygame-BitmapFont.git](https://github.com/xdoko01/Pygame-BitmapFont.git)
        cd Pygame-BitmapFont
        ```
    * **Place the `pgbitmapfont` package:** Ensure the `pgbitmapfont` directory (containing the library's `__init__.py` and other modules) is in your Python project's site-packages directory or within your project structure where Python can import it.

## Usage

Here's a basic example of how to use the Pygame-BitmapFont library in your Pygame project after installing it (either via pip or by placing the package):

```python
import pygame
from pgbitmapfont import BitmapFont

# Initialize Pygame
pygame.init()

# Set up display
screen_width = 800
screen_height = 600
screen = pygame.display.set_mode((screen_width, screen_height))
pygame.display.set_caption("Pygame-BitmapFont Example")

# Load the font
font = BitmapFont("path/to/your/font.json")

# Text to render
text = "Hello, Pygame!"
text_position = (100, 100)

# Game loop
running = True
while running:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False

    # Clear the screen
    screen.fill((0, 0, 0))  # Black

    # Render and blit the text
    screen.blit(font.render(text)[0], text_position)

    # Update the display
    pygame.display.flip()

# Quit Pygame
pygame.quit()
```

## Usage of `bitmapfont-extract` tool

![extractor.png](extractor.png "Extractor tool")

Once the Pygame-BitmapFont (pgbitmapfont) package is installed via `pip`, you can use the following command to run the bitmapfont-extract tool:

```bash
bitmapfont-extract --img font_image.png --out font.json
```

### Controls

 - Select the suitable grid resolution by 'PgUp', 'PgDown'
 - Select the cell with texture by mouse and/or cursor keys
 - Press INSERT and enter the character under which it will be stored.
 - Once done, press RETURN to save and continue.

Tips
 - once saved, the cell is grey

## Changelog

### Release 0.1.6
 * `pygame-ce` used instead of `pygame` due to problems with python 3.14

### Release 0.1.7
 * Dependency on the obsolete `pathlib` PyPI backport removed - it shadowed the stdlib module and broke installs on modern Python. `from pathlib import Path` keeps working, it is the standard library module.
 * `requires-python` raised from `>=3.7` to `>=3.10` - it now matches what `pygame-ce` supports and what this library's own type annotations require
