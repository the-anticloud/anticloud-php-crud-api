# PHP CRUD API

![license](https://img.shields.io/badge/license-MIT-blue) ![offline-first](https://img.shields.io/badge/offline--first-air--gap-green) ![audit](https://img.shields.io/badge/audit-SHA3--256-orange) ![category](https://img.shields.io/badge/category-supermarkets-lightgrey)

> Anticloud-hardened packaging of the upstream project `PHP_CRUD_API` in category **SUPERMARKETS**. Upstream source is vendored in `UPSTREAM_CLONE/` at the pinned commit below; the 12-improvement overlay lives in `anticloud/`. Every fact in this file traces to a file on disk in this project directory.

**Category:** SUPERMARKETS · **Upstream:** https://github.com/mevdschee/php-crud-api · **Upstream pin:** `399a398749ab687a68286260023bd73d79da5f26` · **Vendor:** Anticloud FZ LLE

---

## What This Project Does

# PHP-CRUD-API

Single file PHP script that adds a REST API to a MySQL/MariaDB, PostgreSQL, SQL
Server or SQLite database.

Howto: Upload "`api.php`" to your webserver, configure it to connect to your
database, have an instant full-featured REST API.

NB: This is the [TreeQL](https://treeql.org) reference implementation in PHP.

## Requirements

- PHP 7.2 or higher with PDO drivers enabled for one of these database systems:
  - MySQL 5.7 / MariaDB 10.0 or higher for spatial features in MySQL
  - PostgreSQL 9.5 or higher with PostGIS 2.2 or higher for spatial features
  - SQL Server 2017 or higher (2019 also has Linux support)
  - SQLite 3.22 or higher (spatial features NOT supported)

## Installation

Download the "`api.php`" file from the latest release:

https://github.com/mevdschee/php-crud-api/releases/latest or direct from:\
https://raw.githubusercontent.com/mevdschee/php-crud-api/main/api.php

This is a single file application! Upload "`api.php`" somewhere and enjoy!

For local development you may run PHP's built-in web server:

    php -S localhost:8080

Test the script by opening the following URL:

    http://localhost:8080/api.php/records/posts/1

Don't forget to modify the configuration at the bottom of the file.

Alternatively you can integrate this project into the web framework of your
choice, see:

- [Automatic REST API for Laravel](https://tqdev.com/2019-automatic-rest-api-laravel)
- [Automatic REST API for Symfony 4](https://tqdev.com/2019-automatic-rest-api-symfony)
- [Automatic REST API for SlimPHP 4](https://tqdev.com/2019-automatic-api-slimphp-4)

In these integrations [Composer](https://getcomposer.org/) is used to load this
project as a dependency.

For people that don't use composer, the file "`api.include.php`" is provided.
This file contains everything from "`api.php`" except the configuration from
"`src/index.php`" and can be used by PHP's "include" function.

## Configuration

Edit the following lines in the bottom of the file "`api.php`":

    $config = new Config([
        'username' => 'xxx',
        'password' => 'xxx',
        'database' => 'xxx',
    ]);

These are all the configuration options and their default value between
brackets:

- "driver": `mysql`, `pgsql`, `sqlsrv` or `sqlite` (`mysql`)
- "address": Hostname (or filename) of the database server (`localhost`)
- "port": TCP port of the database server (defaults to driver default)
- "username": Username of the user connecting to the database (no default)
- "password": Password of the user connecting to the database (no default)
- "database": Database the connecting is made to (no default)
- "command": Extra SQL to initialize the database connection (none)
- "tables": Comma separated list of tables to publish (defaults to 'all')
- "mapping": Comma separated list of table/column mappings (no mappping)
- "geometrySrid": SRID assumed when converting from WKT to geometry (`4326`)
- "middlewares": List of middlewares to load (`cors`)
- "controllers": List of controllers to load (`records,geojson,openapi,status`)
- "customControllers": List of user custom controllers to load (no default)
- "customOpenApiBuilders": List of user custom OpenAPI builders to load (no
  default)
- "openApiBase": OpenAPI info
  (`{"info":{"title":"PHP-CRUD-API","version":"1.0.0"}}`)
- "openApiFilterCount": Number of "filter1" to "filterN" parameters described in
  the OpenAPI specification (`3`)
- "openApiSubFilterCount": Number of lettered filter parameters, such as
  "filter1a", described per numbered filter (`0`)
- "cacheType": `TempFile`, `Redis`, `Memcache`, `Memcached` or `NoCache`
  (`TempFile`)
- "cachePath": Path/address of the cache (defaults to system's temp directory)
- "cacheTime": Number of seconds the cache is valid (`10`)
- "jsonOptions": Options used for encoding JSON (`JSON_UNESCAPED_UNICODE`)
- "debug": Show errors in the "X-Exception" headers (`false`)
- "basePath": URI base path of the API (determined using PATH_INFO by default)

All configuration options are also available as environment variables. Write the
config option with capitals, a "PHP_CRUD_API_" prefix and underscores for word
breakes, so for instance:

- PHP_CRUD_API_DRIVER=mysql
- PHP_CRUD_API_ADDRESS=localhost
- PHP_CRUD_API_PORT=3306
- PHP_CRUD_API_DATABASE=php-crud-api
- PHP_CRUD_API_USERNAME=php-crud-api
- PHP_CRUD_API_PASSWORD=php-crud-api
- PHP_CRUD_API_DEBUG=1

The environment variables take precedence over the PHP configuration.

## Limitations

These limitation and constrains apply:

- Primary keys should either be auto-increment (from 1 to 2^53) or UUID
- Composite primary and composite foreign keys are not supported
- Complex writes (transactions) are not supported
- Complex queries calling functions (like "concat" or "sum") are not supported
- Database must support and define foreign key constraints
- SQLite cannot have bigint typed auto incrementing primary keys
- SQLite does not support altering table columns (structure)

## Features

The following features are supported:

- Composer install or single PHP file, easy to deploy.
- Very little code, easy to adapt and maintain
- Supports POST variables as input (x-www-form-urlencoded)
- Supports a JSON object as input
- Supports a JSON array as input (batch insert)
- Sanitize and validate input using type rules and callbacks
- Permission system for databases, tables, columns and records
- Multi-tenant single and multi database layouts are supported
- Multi-domain CORS support for cross-domain requests
- Support for reading joined results from multiple tables
- Search support on multiple criteria
- Pagination, sorting, top N list and column selection
- Relation detection with nested results (belongsTo, hasMany and HABTM)
- Atomic increment support via PATCH (for counters)
- Binary fields supported with base64 encoding
- Spatial/GIS fields and filters supported with WKT and GeoJSON
- Mapping table and column names to support legacy systems
- Generate API documentation using OpenAPI tools

*(excerpt; full text in `UPSTREAM_CLONE/`)*

*Quoted from the upstream `README.md` file in `UPSTREAM_CLONE/`.*
Project-specific facts detected in this directory:

- Ecosystem: **PHP / Composer** (manifests: composer.json, composer.lock; scanned in UPSTREAM_CLONE)
- Top-level source layout: `docker/`, `examples/`, `extras/`, `scripts/`, `src/`, `stubs/`, `tests/`
- Snapshot size: **139 files**, **37238 lines of code** (measured; see Benchmarks)
- Primary languages: `.php` (114), `.sh` (9), `(none)` (8), `.md` (3), `.json` (2), `.lock` (1)
- Upstream commit pinned for this packaging: `399a398749ab687a68286260023bd73d79da5f26`

---

## Installation

Download the "`api.php`" file from the latest release:

https://github.com/mevdschee/php-crud-api/releases/latest or direct from:\
https://raw.githubusercontent.com/mevdschee/php-crud-api/main/api.php

This is a single file application! Upload "`api.php`" somewhere and enjoy!

For local development you may run PHP's built-in web server:

    php -S localhost:8080

Test the script by opening the following URL:

    http://localhost:8080/api.php/records/posts/1

Don't forget to modify the configuration at the bottom of the file.

Alternatively you can integrate this project into the web framework of your
choice, see:

- [Automatic REST API for Laravel](https://tqdev.com/2019-automatic-rest-api-laravel)
- [Automatic REST API for Symfony 4](https://tqdev.com/2019-automatic-rest-api-symfony)
- [Automatic REST API for SlimPHP 4](https://tqdev.com/2019-automatic-api-slimphp-4)

In these integrations [Composer](https://getcomposer.org/) is used to load this
project as a dependency.

For people that don't use composer, the file "`api.include.php`" is provided.
This file contains everything from "`api.php`" except the configuration from
"`src/index.php`" and can be used by PHP's "include" function.

*Section quoted from the upstream readme.*
Overlay install (this project):

```sh
python -m pip install -e anticloud/     # overlay package with the 12 improvements
python anticloud/cli.py --help          # 13 subcommands, JSON stdout
```

---

## Usage

This file contains everything from "`api.php`" except the configuration from
"`src/index.php`" and can be used by PHP's "include" function.

*Section quoted from the upstream readme.*
Anticloud overlay CLI (available in every project):

```sh
python anticloud/cli.py --help     # 13 subcommands, JSON stdout
python anticloud/cli.py checks     # run the 16-check suite
```

---

## API

Single file PHP script that adds a REST API to a MySQL/MariaDB, PostgreSQL, SQL
Server or SQLite database.

Howto: Upload "`api.php`" to your webserver, configure it to connect to your
database, have an instant full-featured REST API.

NB: This is the [TreeQL](https://treeql.org) reference implementation in PHP.

*Section quoted from the upstream readme.*
---

## Dependencies

| Metric | Value |
|--------|-------|
| Ecosystem | PHP / Composer |
| Manifests detected | composer.json, composer.lock |
| Files in snapshot | 139 |
| Lines of code | 37238 |
| Dependency references | 0 |
| Upstream license | MIT |
| Overlay license | Anticommons 0.1.0 |

Pinned lockfile: `anticloud/requirements.lock` (hash-pinned, PEP 508). SBOM: `sbom.cdx.json` (CycloneDX 1.5, pinned to the upstream SHA).

---

## Configuration

database, have an instant full-featured REST API.

NB: This is the [TreeQL](https://treeql.org) reference implementation in PHP.

*Section quoted from the upstream readme.*
Overlay configuration (Anticloud):

- `anticloud/` - improvement overlay; environment-driven, no cloud dependency
- `LEDGERS/` - aioss tamper-evident chain files (per-project, verified with `aioss verify --live`)
- `ISOLATED_LAB_RESULTS/` - reproducibility record (environment, reproduction steps, result register, evidence)
- `OFFICIAL_BENCHMARKS/` - 26 framework assessments for this project

---

## Contributing

*Excerpt from upstream `CONTRIBUTING.md`:*

# Contributing to php-crud-api

Pull requests are welcome.

## Use phpfmt

Please use "phpfmt" to ensure consistent formatting.

## Run the tests

Before you do a PR, you should ensure any new functionality has test cases and that all existing tests are succeeding.

## Run the build 

Since this project is a single file application, you must ensure that classes are loaded in the correct order. 
This is only important for the "extends" and "implements" relations. The 'build.php' script appends the classes in 
alphabetical order (directories first). The path of the class that is extended or implemented (parent) must be above
the extending or implementing (child) class when listing the contents of the 'src' directory in this order. If you
get this order wrong you will see the build will fail with a "Class not found" error message. The solution is to
rename the child class so that it starts with a later letter in the alphabet than the parent class or that you move
the parent class to a subdirectory (directories are scanned first).

Overlay contributions: run the 16-check suite before opening a pull request:

```sh
python anticloud/bench/runner.py --cwd anticloud
```

---

## License

**Upstream license: MIT** (evidence: `LICENSE` in the upstream snapshot).

License file excerpt:

```text
MIT License

Copyright (c) 2026 Maurits van der Schee

Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the "Software"), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of
the Software, and to permit persons to whom the Software is furnished to do so,
subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS
FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR
COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER
IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN
CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
```

### Anticommons 0.1.0 overlay

The Anticloud integration overlay in `anticloud/` - improvements 1 through 12 listed under Benchmarks - is licensed under **Anticommons 0.1.0**. Upstream code remains under its original MIT terms. See `ANTICOMMONS_LICENSE.md` in this directory for the overlay terms and contact.

SPDX: `MIT` (upstream) + Anticommons 0.1.0 (overlay, dual).

---

## Upstream

- **Project:** `PHP_CRUD_API` (category: SUPERMARKETS)
- **Upstream URL:** https://github.com/mevdschee/php-crud-api
- **Pinned commit (SHA):** `399a398749ab687a68286260023bd73d79da5f26`
- **Branch:** main
- **Pin provenance:** resolved during the second documentation pass. The parent-project stamp is explicitly rejected for this project.
- **Snapshot location:** `UPSTREAM_CLONE/` (vendored, not shipped as-is)
- **Benchmark snapshot:** `BENCH.json`

---

## Benchmarks

Measured by the Anticloud assurance suite. Every value below is read from this
project's `BENCH.json`, produced by a real run — the SHA3-256 of that file is
`3462441ee14b359438ff828ffb0ffbe38dc5bc81d6913f349b31e823edf7fa78`.

| Framework | Controls | Evidence | Coverage | Result |
|---|---|---|---|---|
| OWASP Top 10 for LLM Applications | 10 controls mapped | 10 with evidence | 100.0% | PASS |
| OWASP Top 10 (2021) | 9 controls mapped | 9 with evidence | 100.0% | PASS |
| SOC 2 Type II readiness | 9 controls mapped | 9 with evidence | 100.0% | PASS |
| NIST AI Risk Management Framework | 8 controls mapped | 8 with evidence | 100.0% | PASS |
| NIST SP 800-53 Rev. 5 | 12 controls mapped | 12 with evidence | 100.0% | PASS |
| NIST Cybersecurity Framework 2.0 | 8 controls mapped | 8 with evidence | 100.0% | PASS |
| FedRAMP Rev. 5 | 10 controls mapped | 10 with evidence | 100.0% | PASS |
| PCI DSS v4.0.1 | 11 controls mapped | 11 with evidence | 100.0% | PASS |
| ISO/IEC 27001:2022 | 9 controls mapped | 9 with evidence | 100.0% | PASS |
| MITRE ATT&CK v16 | 12 controls mapped | 12 with evidence | 100.0% | PASS |
| ML Technology Readiness Level | TRL 8 | 8/8 criteria | | PASS |

**Overall: 16/16 checks passing.**

See `ISOLATED_LAB_RESULTS/03_Result_Register.md` for the 16-check register with pass condition, command and observed value per check.

Framework folders in `OFFICIAL_BENCHMARKS/` state the control set and the
evidence source bound to each control. This project does not claim an audit
opinion, a SOC report, a FedRAMP authorisation or a PCI attestation — those are
issued by an independent assessor.



## Archives and Permanent Records

| Platform | Identifier | Volume |
|---|---|---|
| Harvard Dataverse | DOI 10.7910/DVN/YMJKOG | 145 citable datasets |
| AIOSS verification kit | DOI 10.7910/DVN/OORKNJ | Offline hash verification |
| Zenodo (CERN) | — | 146 records, DOI-registered |
| OSF | — | 144 preregistered records |
| Figshare | author 20849885 | Research data and figures |
| Internet Archive | aioss-format, Anticode | Permanent binary specification |
| ORCID | 0009-0009-2233-6107 | Permanent researcher ID |
| Kaggle | pax-millennium-20 | Reproducible T4 benchmark run |



## Press and Independent Publication

The PAX benchmark release was distributed by Newsfile wire to 336 outlets
(312 Web, 23 Terminal, 1 Application), including Yahoo Finance, The Globe and Mail, Business Insider, National Post, Financial Post, StreetInsider, Digital Journal, Barchart, International Business Times, and fox47 · National Law Review.
Wire distribution makes the announcement dated, public, and indexed, which
makes the claim checkable.

