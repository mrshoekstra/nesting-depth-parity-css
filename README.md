# 🪆 Nesting Depth Parity CSS <picture><img alt="CSS" src="https://img.shields.io/badge/CSS-663399"></picture>

A tiny pure CSS trick that exposes the nesting depth parity through a custom property named `--evenodd`.

The variable automatically alternates between `odd` and `even` at each nesting level, allowing nested elements such as blockquotes, comments, lists, trees, menus, and other hierarchical structures to alternate their styling without JavaScript, preprocessors, extra classes, or hardcoded depth selectors.

## ✨ Features

* Pure vanilla CSS
* No JavaScript
* No build tools
* No preprocessors
* Unlimited nesting depth
* Can drive any CSS property
* Useable with any nested element structure
* Easy to integrate into existing projects

## 🚀 Usage

### Using `if()`

```css
blockquote {
	--evenodd: odd;
	background: if(
		style(--evenodd: odd): whitesmoke;
		else: snow;
	);

	@container style(--evenodd: odd) {
		--evenodd: even;
	}
}
```

### Without `if()`

```css
blockquote {
	--evenodd: odd;
	background: whitesmoke;

	@container style(--evenodd: odd) {
		--evenodd: even;
		background: snow;
	}
}
```

### How it works

1. Each element starts with `--evenodd: odd`.
2. When an element is nested inside another element whose `--evenodd` value is `odd`, a style container query changes the nested element to `even`.
3. The process repeats recursively, causing every nesting level to alternate between `odd` and `even`.
4. This allows descendant elements to react to nesting depth parity entirely through CSS.

## 🌐 Browser Support

This project relies only on:

* CSS at-rule `@container` ✅ [Baseline Widely available](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/At-rules/@container)
* CSS function `var()` ✅ [Baseline Widely available](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Values/var)
* CSS function `if()` 🔶 [Limited availability](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Values/if) (optional)

> [!IMPORTANT]
> The core functionality works without `if()`. The `if()` example is provided as a more concise alternative for browsers that support it.

> [!NOTE]
> Since the implementation is based entirely on modern CSS features, there are no runtime dependencies and no JavaScript fallback is required.

## 🧠 Philosophy

CSS already understands document hierarchy. This project explores how far native CSS can be pushed to derive useful structural information without requiring JavaScript.

The goal is simple:

> Expose nesting parity as a reusable CSS variable and let authors decide how to use it.

## ⚖️ License

Code released under the [MIT license](LICENSE.md).

## ❤️ Support

If you found this code helpful, please consider making a donation or become a sponsor to support my work. Even a small donation can make a big difference!
