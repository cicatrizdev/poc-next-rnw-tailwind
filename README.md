# Next.js App with React Native Web and TailwindCSS

## Easy mode

- `yarn create next-app --example with-react-native-web YOUR-APP-NAME`;
- `cd YOUR-APP-NAME`
- `yarn add twrnc next-transpile-modules next-compose-plugins`
- go to `next.config.js` and change the content to:

```
const withPlugins = require('next-compose-plugins');
const withTM = require('next-transpile-modules')(['twrnc']);

module.exports = withPlugins([withTM], {
	webpack: (config) => {
		config.resolve.alias = {
			...(config.resolve.alias || {}),
			// Transform all direct `react-native` imports to `react-native-web`
			'react-native$': 'react-native-web',
		};
		config.resolve.extensions = ['.web.js', '.web.ts', '.web.tsx', ...config.resolve.extensions];
		return config;
	},
});
```

- run `yarn next``
- enjoy your Next.js app with React Native Web components and tailwindcss (with twrnc)
