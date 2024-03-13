# Snapshot tests for Grandinė

Test paths are structured as follows:

[`<preset>`]`/`[`<configuration>`]`/ <anchor> / <other data> / <test case>`

Apart from `<test case>`, none of these are self-describing.
The test runner is expected to have code to handle each variation.
This may change in the future.

A test case consists of pairs of `*.request` and `*.response` files.
Requests are performed in lexicographical order.
Each test case is run in isolation.

All requests must use HTTP/1.0.
This is to keep the test runner simple.
This may change in the future.

`*.response` files do not have to be written by hand.
They can be generated and updated by setting `http_api::snapshot_tests::UPDATE_RESPONSES` to `true`.

Self-contained requests without side effects should be grouped into test cases named `*read-only` to save resources.
The test runner treats them specially by always running all requests in them for better error reporting.
This should still be faster than having individual test cases for each request.
This assumes the requests are in fact read-only.

[`<preset>`]:        https://github.com/ethereum/consensus-specs/tree/9ec97badf3ee924aae0ee92cf6c957fbe3b7ef4b/presets
[`<configuration>`]: https://github.com/ethereum/consensus-specs/tree/9ec97badf3ee924aae0ee92cf6c957fbe3b7ef4b/configs
