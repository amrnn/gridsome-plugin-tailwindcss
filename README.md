# gridsome-plugin-tailwindcss

[Example project](http://github.com/brandonpittman/gridsome-plugin-tailwindcss-ffs)

This plugin will add [Tailwind](http://tailwindcss.com) to your
[Gridsome](http://gridsome.org) project. I've gone ahead and automatically
imported the default `tailwind.css` file from the Tailwind npm package. It's just add a CSS file that includes:

```postcss
@tailwind base;
@tailwind components;
@tailwind utilities;
```

You may be wondering, "Where do I add global CSS?!" Short answer, you don't.
Long answer, read the Tailwind docs on [creating plugins][plugins] and use
`tailwind.config.js` to add base styles and create components/utilities there.

**If you need to create `tailwind.config.js`, run `./node_modules/.bin/tailwind init` to create one.**

[plugins]: https://tailwindcss.com/docs/plugins/#app

To use this plugin, run `npm install -D gridsome-plugin-tailwindcss` add the following to your `gridsome.config.js`.


```javascript
modules.exports = {
	plugins: [
		{
			use: 'gridsome-plugin-tailwindcss',
			options: {
			tailwindConfig: './some/file/js',
			purgeConfig: {},
			presetEnvConfig: {},
			shouldPurge: true,
			shouldImport: true,
			shouldTimeTravel: true,
			shouldPurgeUnusedKeyframes: true,
		}
	}
  ]
}
```
If you don't supply a config file path, Tailwind defaults will be used.

The following PostCSS plugins are also included with this plugin:

## PurgeCSS

[PurgeCSS](https://www.purgecss.com/with-postcss) is enabled by default. If you'd like to disable it, pass `shouldPurge:
false` to the plugin options object.

## postcss-import

[postcss-import](https://github.com/postcss/postcss-import) included by default. Pass `shouldImport: false` to disable.

## postcss-preset-env

[postcss-preset-env](https://github.com/csstools/postcss-preset-env) included by default. Pass `shouldTimeTravel: false` to disable. You may also pass a config object to the plugin as `presetEnvConfig`.

With this one plugin, you should be ready to use Tailwind right away. Keep your
customization to `tailwind.config.js` whenever possible, but you can use the
full power of Tailwind (including `@apply`) in your Vue components when
necessary.

Happy coding!
