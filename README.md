# Character

A library for working with character cards.

## Installation

To install the library, use npm:

```sh
npm install @openrouter/character
```

## Usage

Here's a simple example of how to use the library:

```javascript
import { Character } from '@openrouter/character';

const file = new File(['{"name": "John Doe"}'], 'character.json', { type: 'application/json' });

Character.fromFile(file).then((character) => {
  console.log(character.name); // Output: John Doe
});
```

## API Documentation

### `Character`

#### Properties

- `metadata`: The metadata of the character.
- `fallbackAvatar`: The fallback avatar of the character.

#### Methods

- `static fromFile(file: File): Promise<Character>`: Creates a `Character` instance from a file.
- `avatar`: Returns the avatar of the character.
- `description`: Returns the description of the character.
- `name`: Returns the name of the character.

## Comprehensive Example

Here's a comprehensive example demonstrating the `Character` class:

```javascript
import { Character } from '@openrouter/character';

const jsonFile = new File(['{"name": "John Doe", "description": "A brave warrior"}'], 'character.json', { type: 'application/json' });
const pngFile = new File([/* PNG file data */], 'character.png', { type: 'image/png' });
const webpFile = new File([/* WEBP file data */], 'character.webp', { type: 'image/webp' });

Promise.all([
  Character.fromFile(jsonFile),
  Character.fromFile(pngFile),
  Character.fromFile(webpFile)
]).then(([jsonCharacter, pngCharacter, webpCharacter]) => {
  console.log(jsonCharacter.name); // Output: John Doe
  console.log(jsonCharacter.description); // Output: A brave warrior

  console.log(pngCharacter.avatar); // Output: Base64 encoded PNG avatar
  console.log(webpCharacter.avatar); // Output: Base64 encoded WEBP avatar
});
```

## Acknowledgements

- https://github.com/SillyTavern/SillyTavern
- https://github.com/ZoltanAI/character-editor
- https://github.com/AVAKSon/character-editor

## License

MIT
