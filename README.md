# JSON to Go Struct

Paste JSON and generate Go structs with exported CamelCase field names, correct types, and json struct tags that preserve the original keys. Handles nested and anonymous structs and arrays of objects. Everything runs in your browser with no external dependencies and works offline.

**Live demo:** https://0xelitesystem.github.io/json-to-go-struct/

## Use

1. Paste JSON into the JSON box, or click Load sample.
2. Set the root struct name, and choose pointer types for null values and named or inline nested structs.
3. Click Generate structs, or press Ctrl or Cmd + Enter.
4. Click Copy and paste the structs into your Go code.

## Why this exists

Writing Go structs and json tags by hand for a large API response is slow and error-prone, and pasting that response into a hosted converter can expose real data. This is one HTML file with no tracking and no network calls, MIT licensed, that does the conversion in your browser.

## Features

- Exported field names: `user_id` becomes `UserID`, `full-name` becomes `FullName`. Common initialisms (ID, URL, API, UUID, HTTP, JSON, and more) are capitalized the Go way.
- Type inference: `string`, `int`, `float64`, `bool`, `interface{}` for null, nested structs for objects, slices for arrays.
- json struct tags keep the exact original key, for example `` `json:"user_id"` ``.
- Nested objects become named struct types (or inline anonymous structs, your choice).
- Arrays of objects merge their fields across every element, so optional keys still appear in the generated struct.
- Options: pointer types for nullable fields, inline versus named nested structs, and a custom root struct name.
- Copy button, dark-mode toggle, keyboard friendly (Ctrl or Cmd + Enter to generate).

## How it works

The tool parses your JSON with the browser's built-in `JSON.parse`, then walks the value tree. Objects become struct types, arrays become slices, and scalars map to Go types (whole numbers become `int`, decimals become `float64`). Field names are CamelCased from the original key while the original key is preserved in a json tag. For arrays of objects, every element is merged into one representative shape so the generated struct covers all observed fields. No network requests are made.

## Privacy

Everything happens locally in your browser. Your JSON is never uploaded, logged, or sent anywhere. There are no external scripts, fonts, or stylesheets, so the page works offline. You can confirm by opening your browser DevTools and watching the network tab: no requests are made. The one thing the page stores is your light or dark theme choice, saved in `localStorage` under the key `theme`.

## Run locally

```
git clone https://github.com/0xelitesystem/json-to-go-struct
cd json-to-go-struct
```

Open `index.html` in any modern browser. Or serve the folder with `python -m http.server` and visit http://localhost:8000.

## Build

No build step. The whole tool is one `index.html` with inline CSS and JavaScript and no dependencies.

## More

Part of a catalog of single-file browser tools and plain-language references, all MIT licensed and dependency-free: [0xelitesystem.github.io](https://0xelitesystem.github.io/). Built by [elitesystem.ai](https://elitesystem.ai).

## License

MIT. Copyright 0xelitesystem 2026.
