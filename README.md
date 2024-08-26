# Github action "testim-ghaction"

## Purpose

Perform [Testim](https://www.testim.io) end-to-end tests

## Details

This action runs all tests associated with the label in `testim_test` on [Testim](https://www.testim.io).

## Prerequisites

None

## Usage

Here is how you can call this action:

```yaml
on: 
  workflow_call:
    inputs:
      testim_tests:
        description: List of Testim test labels
        required: true
        type: string

jobs:

  end2end_tests:
    name: End-to-end testing with Testim
    runs-on: ubuntu-latest
    strategy:
      max-parallel: 1
      matrix:
        testim_test: ${{ fromJson(inputs.testim_tests) }}
    uses: ajilach/testim-ghaction@v1.0.0
    with:
      testim_test: matrix.testim_test

```
