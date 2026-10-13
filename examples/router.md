# Example: triage-router

## Before
The agent jumped straight to prompt wording even though the real problem was an old file still in scope.

## After
The router picked `folder-hygiene` first because the failure was mixed scope, not weak wording.

## Result
The first fix matched the first failure.

## Limitation
A router cannot repair the source. It only prevents the wrong skill from being applied first.
