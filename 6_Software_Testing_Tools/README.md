
# 6 — Software Testing Tools Practice

The lab provides a repository containing an application with four test cases. The exercise is to run the tests, find the bug, fix it using AI-assisted ("vibe") coding, retest, and share the fixed repository link.

## What this folder needs

| Item | Status |
|---|---|
| Link to the provided application repository | To be added |
| Screenshot of the four tests failing before the fix | To be added |
| The diagnosis — what the bug actually was | To be added |
| Screenshot of the AI tool being used to produce the fix | To be added |
| Screenshot of the tests passing after the fix | To be added |
| Link to the fixed repository | To be added |

## Links

**Provided repository:** `<add link here>`

**Fixed repository:** `<add link here>`

## Suggested screenshots

| # | Filename | What it should show |
|---|---|---|
| 1 | `01-tests-failing.png` | Test runner output with the failing case(s) |
| 2 | `02-bug-located.png` | The offending line in the source |
| 3 | `03-ai-fix-suggestion.png` | The AI tool proposing the patch |
| 4 | `04-patch-applied.png` | The diff or the corrected code |
| 5 | `05-tests-passing.png` | All four tests passing after the fix |

## Process to follow

Read the provided README first. It explains what the application does, how to run the tests, and how the testing process is meant to work. Follow it rather than guessing.

Run the tests before changing anything. The failing output is evidence, and without a "before" screenshot the "after" proves nothing.

Read the failure message properly. Identify which test failed, what input was used, and what the expected and actual results were. This usually helps locate the bug.

Use the AI tool with the failure as context. Provide the failing test and the function or code related to the failure rather than simply asking the AI to "fix the code".

Verify the fix yourself. An AI-generated patch that makes a test pass is not automatically correct. Check that the patch fixes the actual cause of the bug.

Retest the complete test suite, not only the test that originally failed. This helps ensure that the fix does not introduce a regression.

Commit the fix with a meaningful commit message that identifies the bug, then record the fixed repository link above.

## Write-up

When the fix is completed, add a short note covering:

- What the four test cases check.
- Which test case failed and why.
- What the root cause of the bug was.
- What the patch changed.
- Whether the AI tool's first suggestion was correct or required modification.
- Whether all four test cases passed after the fix.

The purpose of this activity is to demonstrate the complete testing process: identifying a failure, locating the cause, using AI-assisted coding to develop a fix, applying the patch, and retesting the application.
