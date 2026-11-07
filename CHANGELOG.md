# Changelog

## [Unreleased]

## [1.0.1] - 2026-11-07

### Fixed
- Match DVD titles without case sensitivity (#18).

## [1.0.0] - 2026-11-07

### Added
- Print the cart contents and handle an empty cart.
- Search DVDs by a substring of their title.
- Calculate the total after a percentage discount.
- Unit tests and use-case documentation.

### Changed
- Move the application classes into the `aims` package.
- Show the added-DVD message in Vietnamese.

### Fixed
- Reject the 21st DVD when the cart already contains 20 DVDs (#7).
- Return the discounted total and reject percentages outside 0–100.
