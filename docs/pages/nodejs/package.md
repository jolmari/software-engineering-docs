%% #-🪴weedy %%
[[Unsorted]]
# Package management

## Enforce specific nodejs version

There are two steps to enforcing a specific `nodejs` version for your project:

1. Specify the version to use
2. Prevent incompatible version usage

### Specify the version to use

The way to specify the version of `nodejs` depends on the package manager you are using.

#### Volta

Install [Volta](https://volta.sh/) Add the following block to your `package.json` file. Volta will recognize the version and switch to it automatically
when you run script commands.

```json
"volta": {
  "node": "major.minor.patch"
}
```

#### Node Version Switcher (nvs)

Install [NVS](https://github.com/jasongin/nvs). Add a `.node-version` file in the root of your project with the version you want to use.

```sh
major.minor.patch
```

Run the following command to switch to the specified version:

```sh
nvs auto .
```

### Prevent incompatible version usage

To prevent either `npm` or `yarn` from using a non-compatible `nodejs` version, you can enforce the checking
by adding a `.npmrc` file in the root of your project with the following content:

```sh
engine-strict=true
```

Add the following block to your `package.json` file:

```json
"engines": {
  "node": "major.minor.patch"
}
```

The engines-block defines the version required to successfully build and run the project, whereas the other version specifications
define the version used to develop the project. The difference is semantic, but it explains why ex. volta toolchain does not respect 
the engines-block version.

Running package manager commands will now fail with incompatible versions, an example of the error message is:

```sh
> yarn install
yarn install v1.22.19
[1/5] Validating package.json...
error lumoone@1.0.0: The engine "node" is incompatible with this module. Expected version "20.12.1". Got "20.12.2"
error Found incompatible module.
```