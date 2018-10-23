# Moneytree TSLint shared configuration

TSLint configuration that covers both safety and code-style, as used by [Moneytree](https://www.getmoneytree.com/).

## How to setup

In your project, install this configuration:

```sh
npm install --save-dev @moneytree/tslint-rules
```
or
```
yarn add --dev @moneytree/tslint-rules
```

Choose a configuration to use in your project (or a folder somewhere inside your project). Available options:

- `typescript`: Recommended base TypeScript configuration.
- `react`: Extends `typescript` to specialize for React.

Now refer to that configuration in your own TSLint configuration file, by extending from it:

YAML:

```yaml
extends: 
  - @moneytree/tslint-rules
```

JSON:

```json
{
  "extends": ["@moneytree/tslint-rules"]
}
```

> Add "/react" for React projects

## Fine-tuning

If you find that your project needs slightly different rules, or if you introduce this configuration into an existing
project that may break too many rules, you can override the configuration. Especially in the latter case, we would
suggest leaving the rule in place, but turning it into a warning instead, so that you can gradually update your code
base and in the future turn that rule into an error again.

All rules are defined as an object with two value: `severity` and `options`.
The severity is  the level at which you want to apply the rule:

- none: do not enforce rule
- warning: only prints, does not make the lint check fail
- error: the lint check will fail

The options will depends on the rule you want to change. Since we are using several ruleset you better us Google.

To change a rule, simply rewrite the rule in your own configuration file, and adjust the level as you wish.

```
rules:
  <rule-name>:
    severity: error
    options:
      really: true
```

## Additional ruleset

Depending on additional libraries you use, like testing frameworks, there may be some very interesting TSLint ruleset
for your project that you may want to add to your configuration.

## Supported TSLint version

We attempt to keep the rules compatible and complete with regards to the latest version of TSLint. Sometimes we will
inevitably fall behind a little. If you want to know which versions of TSLint we cover, please refer to the version of
the TSLint peer-dependency in [package.json](./package.json).

## Contributing

### Versioning

We try to be [semver](https://semver.org/)-ish in how we version this project. To create a version-bump commit, simply
run `npm version patch`, `npm version minor` or `npm version major`.

*patch* should get bumped when:

- New configuration file variations are introduced (like `react` in the example above).

*minor* should get bumped when:

- Rules are changed.
- Rules are added.
- The `tslint` peer-dependency's minimal version is raised (which is usually when rules are added).

*major* should get bumped when:

- A major version bump of TSLint occurs that has significant impact on the users of this configuration.
- A massive overhaul of the project happens, implying changes to installation and/or integration.
- New peer-dependencies are required.

## License

MIT