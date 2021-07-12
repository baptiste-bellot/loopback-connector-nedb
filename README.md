# loopback-connector-nedb

The unofficial NeDB connector for the LoopBack framework. This is currently a rough fork of MongoDB driver migrated to NeDB as the db interface should be compatible for basic feature.
It is a work in progress.


## Installation

In your application root directory, enter this command to install the connector:

```sh
npm install loopback-connector-nedb --save
```

This installs the module from npm and adds it as a dependency to the application's `package.json` file.

If you create a NeDB data source using the data source generator as described below, you don't have to do this, since the generator will run `npm install` for you.

## Supported versions

**Starting from the version 6.0.0, this connector is no longer compatible with LoopBack 3. Please use the latest 5.x version in your LoopBack 3 applications.**

This module adopts the [Module Long Term Support (LTS)](http://github.com/CloudNativeJS/ModuleLTS) policy, with the following End Of Life (EOL) dates:

| Version    | Status               | Published | EOL                  | LoopBack | Juggler  |
| ---------- | -------------------- | --------- | -------------------- | ---------|----------|
| 6.x        | Current              | Mar 2021  | Apr 2023 _(minimum)_ | 4        | 4.x      |
| 5.x        | Active LTS           | Jun 2019  | Apr 2023             | 3, 4     | 3.x, 4.x |
| 4.x        | Maintenance LTS      | Nov 2018  | Apr 2021             | 3, 4     | 3.x, 4.x |

## Creating a NeDB data source

For LoopBack 4 users, use the LB4 [Command-line interface](https://loopback.io/doc/en/lb4/Command-line-interface.html) to generate a DataSource with NeDB connector to your LB4 application.

The configuration can be found under `src/datasources/<DataSourceName>.datasource.ts`, basic options shnould look like this:

```ts
const config = {
  name: 'db',
  connector: 'ne',
  root: './database',
  stores: [ 'Users', 'AccessTokens', 'MyModel']
};
```

If your username or password contains special characters like `@`, `$` etc, encode the whole
username or password using [encodeURIComponent](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/encodeURIComponent).

Eg: `pa$$wd` would become `pa%24%24wd`.

### Connection properties

| Property   | Type&nbsp;&nbsp; | Description                                                                                                |
| ---------- | ---------------- | ---------------------------------------------------------------------------------------------------------- |
| connector  | String           | Connector name, either `"loopback-connector-nedb"` or `"nedb"`.                                            |
| name       | String           | Name of the datasource in the app                                                                          |
| root       | String           | Root path of database folder                                                                               |
| stores     | String[]         | Names of the datasource files for collections                                                              |

