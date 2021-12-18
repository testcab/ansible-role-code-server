# Changelog

All notable changes to this ansible role will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).

Versioning of the role is irrelevant to the version of *code-server* you can install. Actually, it installs the latest version of *code-server* by default. And you can also use a lower-versioned role to install a higher-versioned *code-server*. When there are changes to the role, the role version will get updated to the latest version number of *code-server*.

## [Unreleased](https://github.com/testcab/ansible-role-code-server/compare/v4.0.0...HEAD)

### Added
- Support running code-server with privileged port using non-root user.

### Changed
- Check for the latest version of code-server is now done locally.

### Removed
- Remove the weekly auto restart of code-server service.


## [v4.0.0](https://github.com/testcab/ansible-role-code-server/tree/v4.0.0) - 2021-12-11

### Added
- Support code-server v4.
- Allow configuring additional environment variables in role variable `code_server_env`.

### Changed
- Fix check for the latest version of code-server.
- Fix logic for determining whether current version is latest.
- Fix quoting issues in `code_server_password`.
- Fix the clean up task to run only when upgrading code-server.
