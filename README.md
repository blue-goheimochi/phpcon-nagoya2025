# phpcon-nagoya2025

PHPカンファレンス名古屋2025の発表内で実行している `composer update` のデモ環境

```
% tree -L 1
.
├── README.md
├── laravel08
├── laravel09
└── laravel10
```

それぞれ各Laravelのバージョンのもっとも古いバージョンとなっている（PR参照）

# 確認方法

dockerコマンド経由でcomposerコマンドを実行する。

## Laravel9の例

```
cd laravel09
```

カレントディレクトリを移動しておく。

### `composer update guzzlehttp/guzzle --dry-run`

```
docker run --rm -v ${PWD}:/app composer:2.8.5 composer update guzzlehttp/guzzle --dry-run --ansi
```

```
% docker run --rm -v ${PWD}:/app composer:2.8.5 composer update guzzlehttp/guzzle --dry-run --ansi
Loading composer repositories with package information
Updating dependencies
Lock file operations: 0 installs, 1 update, 0 removals
  - Upgrading guzzlehttp/guzzle (7.2.0 => 7.3.0)
Installing dependencies from lock file (including require-dev)
Package operations: 0 installs, 1 update, 0 removals
  - Upgrading guzzlehttp/guzzle (7.2.0 => 7.3.0)
Package fruitcake/laravel-cors is abandoned, you should avoid using it. No replacement was suggested.
70 packages you are using are looking for funding.
Use the `composer fund` command to find out more!
Found 13 security vulnerability advisories affecting 8 packages.
Run "composer audit" for a full list of advisories.
```

### `composer update guzzlehttp/guzzle --with-dependencies --dry-run`

```
docker run --rm -v ${PWD}:/app composer:2.8.5 composer update guzzlehttp/guzzle --with-dependencies --dry-run
```

```
% docker run --rm -v ${PWD}:/app composer:2.8.5 composer update guzzlehttp/guzzle --with-dependencies --dry-run --ansi
Loading composer repositories with package information
Updating dependencies
Lock file operations: 1 install, 7 updates, 0 removals
  - Upgrading guzzlehttp/guzzle (7.2.0 => 7.9.2)
  - Upgrading guzzlehttp/promises (1.4.0 => 2.0.4)
  - Upgrading guzzlehttp/psr7 (1.7.0 => 2.7.0)
  - Upgrading psr/http-client (1.0.1 => 1.0.3)
  - Locking psr/http-factory (1.1.0)
  - Upgrading psr/http-message (1.0 => 2.0)
  - Upgrading ralouphie/getallheaders (2.0.5 => 3.0.3)
  - Upgrading symfony/deprecation-contracts (v2.1.2 => v3.5.1)
Installing dependencies from lock file (including require-dev)
Package operations: 1 install, 7 updates, 0 removals
  - Upgrading symfony/deprecation-contracts (v2.1.2 => v3.5.1)
  - Upgrading psr/http-message (1.0 => 2.0)
  - Upgrading psr/http-client (1.0.1 => 1.0.3)
  - Upgrading ralouphie/getallheaders (2.0.5 => 3.0.3)
  - Installing psr/http-factory (1.1.0)
  - Upgrading guzzlehttp/psr7 (1.7.0 => 2.7.0)
  - Upgrading guzzlehttp/promises (1.4.0 => 2.0.4)
  - Upgrading guzzlehttp/guzzle (7.2.0 => 7.9.2)
Package fruitcake/laravel-cors is abandoned, you should avoid using it. No replacement was suggested.
70 packages you are using are looking for funding.
Use the `composer fund` command to find out more!
Found 13 security vulnerability advisories affecting 8 packages.
Run "composer audit" for a full list of advisories.
```

### `composer update guzzlehttp/guzzle --minimal-changes --with-dependencies --dry-run`

```
docker run --rm -v ${PWD}:/app composer:2.8.5 composer update guzzlehttp/guzzle --minimal-changes
```

```
% docker run --rm -v ${PWD}:/app composer:2.8.5 composer update guzzlehttp/guzzle --minimal-changes --with-dependencies --dry-run --ansi
Loading composer repositories with package information
Updating dependencies
Lock file operations: 1 install, 6 updates, 0 removals
  - Upgrading guzzlehttp/guzzle (7.2.0 => 7.9.2)
  - Upgrading guzzlehttp/promises (1.4.0 => 2.0.4)
  - Upgrading guzzlehttp/psr7 (1.7.0 => 2.7.0)
  - Locking psr/http-factory (1.1.0)
  - Upgrading psr/http-message (1.0 => 1.1)
  - Upgrading ralouphie/getallheaders (2.0.5 => 3.0.3)
  - Upgrading symfony/deprecation-contracts (v2.1.2 => v3.5.1)
Installing dependencies from lock file (including require-dev)
Package operations: 1 install, 6 updates, 0 removals
  - Upgrading symfony/deprecation-contracts (v2.1.2 => v3.5.1)
  - Upgrading psr/http-message (1.0 => 1.1)
  - Upgrading ralouphie/getallheaders (2.0.5 => 3.0.3)
  - Installing psr/http-factory (1.1.0)
  - Upgrading guzzlehttp/psr7 (1.7.0 => 2.7.0)
  - Upgrading guzzlehttp/promises (1.4.0 => 2.0.4)
  - Upgrading guzzlehttp/guzzle (7.2.0 => 7.9.2)
Package fruitcake/laravel-cors is abandoned, you should avoid using it. No replacement was suggested.
70 packages you are using are looking for funding.
Use the `composer fund` command to find out more!
Found 13 security vulnerability advisories affecting 8 packages.
Run "composer audit" for a full list of advisories.
```

### `composer outdated --patch-only --locked --direct`

```
docker run --rm -v ${PWD}:/app composer:2.8.5 composer outdated --patch-only --locked --direct --ansi
```

```
% docker run --rm -v ${PWD}:/app composer:2.8.5 composer outdated --patch-only --locked --direct --ansi
fakerphp/faker          1.10.0 1.10.1 Faker is a PHP library that generates ...
fruitcake/laravel-cors  2.0.5  2.0.5  Adds CORS (Cross-Origin Resource Shari...
Package fruitcake/laravel-cors is abandoned, you should avoid using it. No replacement was suggested.
laravel/framework       9.0.0  9.0.2  The Laravel Framework.
laravel/sanctum         2.14.0 2.14.2 Laravel Sanctum provides a featherweig...
laravel/tinker          2.7.0  2.7.3  Powerful REPL for the Laravel framework.
phpunit/phpunit         9.5.10 9.5.28 The PHP Unit Testing framework.
spatie/laravel-ignition 1.0.0  1.0.11 A beautiful error page for Laravel app...
Color legend:
- patch or minor release available - update recommended
- major release available - update possible
```

### `composer audit`

```
docker run --rm -v ${PWD}:/app composer:2.8.5 composer audit --ansi
```

```
% docker run --rm -v ${PWD}:/app composer:2.8.5 composer audit --ansi
Found 13 security vulnerability advisories affecting 8 packages:
+-------------------+----------------------------------------------------------------------------------+
| Package           | guzzlehttp/guzzle                                                                |
| Severity          | high                                                                             |
| CVE               | CVE-2022-31091                                                                   |
| Title             | Change in port should be considered a change in origin                           |
| URL               | https://github.com/guzzle/guzzle/security/advisories/GHSA-q559-8m2m-g699         |
| Affected versions | >=7,<7.4.5|>=4,<6.5.8                                                            |
| Reported at       | 2022-06-20T22:24:00+00:00                                                        |
+-------------------+----------------------------------------------------------------------------------+
+-------------------+----------------------------------------------------------------------------------+
| Package           | guzzlehttp/guzzle                                                                |
| Severity          | high                                                                             |
| CVE               | CVE-2022-31090                                                                   |
| Title             | CURLOPT_HTTPAUTH option not cleared on change of origin                          |
| URL               | https://github.com/guzzle/guzzle/security/advisories/GHSA-25mq-v84q-4j7r         |
| Affected versions | >=7,<7.4.5|>=4,<6.5.8                                                            |
| Reported at       | 2022-06-20T22:24:00+00:00                                                        |
+-------------------+----------------------------------------------------------------------------------+
+-------------------+----------------------------------------------------------------------------------+
| Package           | guzzlehttp/guzzle                                                                |
| Severity          | high                                                                             |
| CVE               | CVE-2022-31043                                                                   |
| Title             | Fix failure to strip Authorization header on HTTP downgrade                      |
| URL               | https://github.com/guzzle/guzzle/security/advisories/GHSA-w248-ffj2-4v5q         |
| Affected versions | >=7,<7.4.4|>=4,<6.5.7                                                            |
| Reported at       | 2022-06-09T23:36:00+00:00                                                        |
+-------------------+----------------------------------------------------------------------------------+
+-------------------+----------------------------------------------------------------------------------+
| Package           | guzzlehttp/guzzle                                                                |
| Severity          | high                                                                             |
| CVE               | CVE-2022-31042                                                                   |
| Title             | Failure to strip the Cookie header on change in host or HTTP downgrade           |
| URL               | https://github.com/guzzle/guzzle/security/advisories/GHSA-f2wf-25xc-69c9         |
| Affected versions | >=7,<7.4.4|>=4,<6.5.7                                                            |
| Reported at       | 2022-06-09T23:36:00+00:00                                                        |
+-------------------+----------------------------------------------------------------------------------+
+-------------------+----------------------------------------------------------------------------------+
| Package           | guzzlehttp/guzzle                                                                |
| Severity          | high                                                                             |
| CVE               | CVE-2022-29248                                                                   |
| Title             | Cross-domain cookie leakage                                                      |
| URL               | https://github.com/guzzle/guzzle/security/advisories/GHSA-cwmx-hcrq-mhc3         |
| Affected versions | >=7,<7.4.3|>=4,<6.5.6                                                            |
| Reported at       | 2022-05-25T13:21:00+00:00                                                        |
+-------------------+----------------------------------------------------------------------------------+
+-------------------+----------------------------------------------------------------------------------+
| Package           | guzzlehttp/psr7                                                                  |
| Severity          | medium                                                                           |
| CVE               | CVE-2023-29197                                                                   |
| Title             | Improper header validation                                                       |
| URL               | https://github.com/guzzle/psr7/security/advisories/GHSA-wxmh-65f7-jcvw           |
| Affected versions | >=2,<2.4.5|<1.9.1                                                                |
| Reported at       | 2023-04-17T16:00:00+00:00                                                        |
+-------------------+----------------------------------------------------------------------------------+
+-------------------+----------------------------------------------------------------------------------+
| Package           | guzzlehttp/psr7                                                                  |
| Severity          | medium                                                                           |
| CVE               | CVE-2022-24775                                                                   |
| Title             | Inproper parsing of HTTP headers                                                 |
| URL               | https://github.com/guzzle/psr7/security/advisories/GHSA-q7rv-6hp3-vh96           |
| Affected versions | >=2,<2.1.1|<1.8.4                                                                |
| Reported at       | 2022-03-20T13:44:00+00:00                                                        |
+-------------------+----------------------------------------------------------------------------------+
+-------------------+----------------------------------------------------------------------------------+
| Package           | laravel/framework                                                                |
| Severity          | high                                                                             |
| CVE               | CVE-2024-52301                                                                   |
| Title             | Laravel environment manipulation via query string                                |
| URL               | https://github.com/advisories/GHSA-gv7v-rgg6-548h                                |
| Affected versions | <6.20.45|>=7.0.0,<7.30.7|>=8.0.0,<8.83.28|>=9.0.0,<9.52.17|>=10.0.0,<10.48.23|>= |
|                   | 11.0.0,<11.31.0                                                                  |
| Reported at       | 2024-11-12T15:29:00+00:00                                                        |
+-------------------+----------------------------------------------------------------------------------+
+-------------------+----------------------------------------------------------------------------------+
| Package           | league/commonmark                                                                |
| Severity          | high                                                                             |
| CVE               | NO CVE                                                                           |
| Title             | league/commonmark's quadratic complexity bugs may lead to a denial of service    |
| URL               | https://github.com/advisories/GHSA-c2pc-g5qf-rfrf                                |
| Affected versions | <2.6.0                                                                           |
| Reported at       | 2024-12-09T20:42:07+00:00                                                        |
| Advisory ID       | PKSA-fndg-qryc-dyc9                                                              |
+-------------------+----------------------------------------------------------------------------------+
+-------------------+----------------------------------------------------------------------------------+
| Package           | nesbot/carbon                                                                    |
| Severity          | medium                                                                           |
| CVE               | CVE-2025-22145                                                                   |
| Title             | Carbon has an arbitrary file include via unvalidated input passed to             |
|                   | Carbon::setLocale                                                                |
| URL               | https://github.com/advisories/GHSA-j3f9-p6hm-5w6q                                |
| Affected versions | <2.72.6|>=3.0.0,<3.8.4                                                           |
| Reported at       | 2025-01-08T21:03:28+00:00                                                        |
+-------------------+----------------------------------------------------------------------------------+
+-------------------+----------------------------------------------------------------------------------+
| Package           | symfony/http-foundation                                                          |
| Severity          | low                                                                              |
| CVE               | CVE-2024-50345                                                                   |
| Title             | CVE-2024-50345: Open redirect via browser-sanitized URLs                         |
| URL               | https://symfony.com/cve-2024-50345                                               |
| Affected versions | >=2.0.0,<3.0.0|>=3.0.0,<4.0.0|>=4.0.0,<5.0.0|>=5.0.0,<5.1.0|>=5.1.0,<5.2.0|>=5.2 |
|                   | .0,<5.3.0|>=5.3.0,<5.4.0|>=5.4.0,<5.4.46|>=6.0.0,<6.1.0|>=6.1.0,<6.2.0|>=6.2.0,< |
|                   | 6.3.0|>=6.3.0,<6.4.0|>=6.4.0,<6.4.14|>=7.0.0,<7.1.0|>=7.1.0,<7.1.7               |
| Reported at       | 2024-11-05T08:00:00+00:00                                                        |
+-------------------+----------------------------------------------------------------------------------+
+-------------------+----------------------------------------------------------------------------------+
| Package           | symfony/http-kernel                                                              |
| Severity          | medium                                                                           |
| CVE               | CVE-2022-24894                                                                   |
| Title             | CVE-2022-24894: Prevent storing cookie headers in HttpCache                      |
| URL               | https://symfony.com/cve-2022-24894                                               |
| Affected versions | >=2.0.0,<2.1.0|>=2.1.0,<2.2.0|>=2.2.0,<2.3.0|>=2.3.0,<2.4.0|>=2.4.0,<2.5.0|>=2.5 |
|                   | .0,<2.6.0|>=2.6.0,<2.7.0|>=2.7.0,<2.8.0|>=2.8.0,<3.0.0|>=3.0.0,<3.1.0|>=3.1.0,<3 |
|                   | .2.0|>=3.2.0,<3.3.0|>=3.3.0,<3.4.0|>=3.4.0,<4.0.0|>=4.0.0,<4.1.0|>=4.1.0,<4.2.0| |
|                   | >=4.2.0,<4.3.0|>=4.3.0,<4.4.0|>=4.4.0,<4.4.50|>=5.0.0,<5.1.0|>=5.1.0,<5.2.0|>=5. |
|                   | 2.0,<5.3.0|>=5.3.0,<5.4.0|>=5.4.0,<5.4.20|>=6.0.0,<6.0.20|>=6.1.0,<6.1.12|>=6.2. |
|                   | 0,<6.2.6                                                                         |
| Reported at       | 2023-02-01T08:00:00+00:00                                                        |
+-------------------+----------------------------------------------------------------------------------+
+-------------------+----------------------------------------------------------------------------------+
| Package           | symfony/process                                                                  |
| Severity          | high                                                                             |
| CVE               | CVE-2024-51736                                                                   |
| Title             | CVE-2024-51736: Command execution hijack on Windows with Process class           |
| URL               | https://symfony.com/cve-2024-51736                                               |
| Affected versions | >=2.0.0,<3.0.0|>=3.0.0,<4.0.0|>=4.0.0,<5.0.0|>=5.0.0,<5.1.0|>=5.1.0,<5.2.0|>=5.2 |
|                   | .0,<5.3.0|>=5.3.0,<5.4.0|>=5.4.0,<5.4.46|>=6.0.0,<6.1.0|>=6.1.0,<6.2.0|>=6.2.0,< |
|                   | 6.3.0|>=6.3.0,<6.4.0|>=6.4.0,<6.4.14|>=7.0.0,<7.1.0|>=7.1.0,<7.1.7               |
| Reported at       | 2024-11-05T08:00:00+00:00                                                        |
+-------------------+----------------------------------------------------------------------------------+
Found 1 abandoned package:
+------------------------+----------------------------------------------------------------------------------+
| Abandoned Package      | Suggested Replacement                                                            |
+------------------------+----------------------------------------------------------------------------------+
| fruitcake/laravel-cors | none                                                                             |
+------------------------+----------------------------------------------------------------------------------+
```
