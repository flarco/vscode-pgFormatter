# pgFormatter [![Build Status](https://travis-ci.org/bradymholt/vscode-pgFormatter.svg?branch=master)](https://travis-ci.org/bradymholt/vscode-pgFormatter)

A VS Code extension that formats PostgresSQL SQL, using the Perl based [pgFormatter](https://github.com/darold/pgFormatter) tool developed by [Gilles Darold](https://github.com/darold).

## Features

* Supports keywords from SQL-92, SQL-99, SQL-2003, SQL-2008, SQL-2011 and PostgreSQL specifics keywords
* Provides configuration to control formatting style

## Installation

**pgFormatter requires [Perl](https://www.perl.org/) to be installed and available**. You can either add it to your PATH or set the `pgFormatter.perlBinPath` configuration setting.

To install this extension:

1. Press `Ctrl + Shift + X` (`Cmd + Shift + X` on macOS), wait a moment while the list of available extensions is populated
2. Type `pgFormatter` and Click "Install"

## Usage

This extension is made available to files recognized as "SQL" language files in VS Code. Generally, files with the `.sql` extension will be recognized as SQL files. You can use the [files.associations](https://code.visualstudio.com/updates/vMarch#_file-to-language-association) setting to customize which files are recognized as SQL files.

To use pgFormatter, you simply need to run the `editor.action.formatDocument` command which is, by default, mapped to the `Ctrl + K, Ctrl + D` (`Cmd + K, Cmd + D` on macOS) keyboard shortcut.

pgFormatter also works with the `"editor.formatOnSave": true` setting so that when when saving your file, formatting will be automatically performed.

## Configuration

This extension has the following configuration settings:

* `pgFormatter.spaces` - Number of spaces to indent the code (Default: 2)
* `pgFormatter.maxLength` - Maximum length of a query
* `pgFormatter.commaStart` - Use preceding comma in parameter list (Default: false)
* `pgFormatter.commaEnd` - Use trailing comma in parameter list (Default: true)
* `pgFormatter.noComment` - Remove any comments (Default: false)
* `pgFormatter.functionCase` - Case of the function names (Options: ["unchanged", "lowercase", "uppercase", "capitalize"]; Default: "unchanged")
* `pgFormatter.keywordCase` - Case of the reserved keywords (Options: ["unchanged", "lowercase", "uppercase", "capitalize"]; Default: "uppercase")
* `pgFormatter.perlBinPath` - The path to the perl executable (Default: "perl")

### Ignoring Files

To ignore a file and prevent it from being formatted, you can simply add a comment on the first line of the file with the contents: "pgFormatter-ignore". For example:

```
-- pgFormatter-ignore

select id from people;
```
## Sideloading the extension
After making changes to the extension, you might want to test it end to end instead of running it in debug mode. To do this, you can sideload the extension. This can be done by preparing the extension and loading it directly.

1. `npm install -g vsce` to make sure you have vsce installed globally
2. `git clone https://github.com/flarco/vscode-pgFormatter.git` to clone the repo if you havent already done so
3. `cd vscode-pgFormatter`
4. `npm install` to install dependencies if you havent already done so
5. `vsce package` to build the package. This will generate a file with extension `vsix`
6. Run the command `Extensions: Install from VSIX...`, choose the vsix file generated in the previous step