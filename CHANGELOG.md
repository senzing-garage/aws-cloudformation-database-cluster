# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
[markdownlint](https://dlaa.me/markdownlint/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

-

## [1.3.7] - 2023-06-19

### Changed in 1.3.7

- updated to Senzing 3.5.3
- updated docker image

## [1.3.6] - 2023-05-12

### Changed in 1.3.6

- updated to Senzing 3.5.2
- updated docker image

## [1.3.5] - 2023-04-05

### Changed in 1.3.5

- updated to Senzing 3.5.0
- removed Senzing v2 CFT

## [1.3.4] - 2023-01-16

### Changed in 1.3.4

- updated to Senzing 3.4.0
- updated database parameters

## [1.3.3] - 2022-11-01

### Changed in 1.3.3

- updated to Senzing 3.3.2

## [1.3.2] - 2022-10-12

### Changed in 1.3.2

- updated to Senzing 3.3.1

## [1.3.1] - 2022-09-29

### Changed in 1.3.1

- updated to Senzing 3.3.0
- default to Single database

## [1.3.0] - 2022-08-29

### Changed in 1.3.0

- added SecondsBeforeTimeout setting
- updated database engine version
- updated to use the init Postgresql image

## [1.2.5] - 2022-06-10

### Changed in 1.2.5

- added image versions to stack output
- updated to Senzing 3.1.0
- updated images to latest stable versions

## [1.2.4] - 2022-05-11

### Changed in 1.2.4

- updated to Senzing 3.0.0

## [1.2.3] - 2021-11-01

### Added to 1.2.3

- extended subnet

## [1.2.2] - 2021-10-20

### Added to 1.2.2

- updated image version

## [1.2.1] - 2021-10-04

### Added to 1.2.1

- updated lambda error messages

## [1.2.0] - 2021-08-14

### Added to 1.2.0

- Updated for database to be self initializing

## [1.1.0] - 2021-07-12

### Added to 1.1.0

- Ability to select single or multiple databases

## [1.0.1] - 2021-07-12

### Added to 1.0.1

- Force scaling capacity set with a lambda function

## [1.0.0] - 2021-05-12

### Added to 1.0.0

- Initial functionality to deploy:
  - VPC and networking
  - 3 Aurora Postgres serverless database
