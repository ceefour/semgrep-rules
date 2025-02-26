# semgrep-rules

[![powered by semgrep](https://img.shields.io/badge/powered%20by-semgrep-1B2F3D?labelColor=lightgrey&link=https://semgrep.live/&style=flat-square&logo=data%3Aimage%2Fpng%3Bbase64%2CiVBORw0KGgoAAAANSUhEUgAAAA0AAAAOCAYAAAD0f5bSAAAABmJLR0QA/gD+AP+cH+QUAAAACXBIWXMAAA3XAAAN1wFCKJt4AAAAB3RJTUUH5AYMEy0l8dkqrQAAAvFJREFUKBUB5gIZ/QEAAP8BAAAAAAMG6AD9+hn/GzA//wD//wAAAAD+AAAAAgABAQDl0MEBAwbmAf36GQAAAAAAAQEC9QH//gv/Gi1GFQEC+OoAAAAAAAAAAAABAQAA//8AAAAAAAAAAAD//ggX5tO66gID9AEBFSRxAgYLzRQAAADpAAAAAP7+/gDl0cMPAAAA+wAAAPkbLz39AgICAAAAAAAAAAAs+vU12AEbLz4bAAAA5P8AAAAA//4A5NDDEwEBAO///wABAQEAAP//ABwcMD7hAQEBAAAAAAAAAAAaAgAAAOAAAAAAAQEBAOXRwxUAAADw//8AAgAAAAD//wAAAAAA5OXRwhcAAQEAAAAAAAAAAOICAAAABP3+/gDjzsAT//8A7gAAAAEAAAD+AAAA/wAAAAAAAAAA//8A7ePOwA/+/v4AAAAABAIAAAAAAAAAAAAAAO8AAAABAAAAAAAAAAIAAAABAAAAAAAAAAgAAAD/AAAA8wAAAAAAAAAAAgAAAAAAAAAAAAAAAAAAAA8AAAAEAAAA/gAAAP8AAAADAAAA/gAAAP8AAAAAAAAAAAAAAAACAAAAAAAAAAAAAAAAAAAA7wAAAPsAAAARAAAABAAAAP4AAAAAAAAAAgAAABYAAAAAAAAAAAIAAAD8AwICAB0yQP78/v4GAAAA/wAAAPAAAAD9AAAA/wAAAPr9//8aHTJA6AICAgAAAAD8AgAAADIAAAAAAP//AB4wPvgAAAARAQEA/gEBAP4BAQABAAAAGB0vPeIA//8AAAAAAAAAABAC+vUz1QAAAA8AAAAAAwMDABwwPu3//wAe//8AAv//ABAcMD7lAwMDAAAAAAAAAAAG+vU0+QEBAvUB//4L/xotRhUBAvjqAAAAAAAAAAAAAQEAAP//AAAAAAAAAAAA//4IF+bTuuoCA/QBAQAA/wEAAAAAAwboAP36Gf8bMD//AP//AAAAAP4AAAACAAEBAOXQwQEDBuYB/foZAAAAAAD4I6qbK3+1zQAAAABJRU5ErkJggg==)](https://semgrep.dev/)
[![r2c community slack](https://img.shields.io/badge/slack-join-green?style=flat-square)](https://r2c.dev/slack)

| branch | using semgrep docker image | test status          |
| ------------ | ------------------------ | -------------------- |
| `develop` | `returntocorp/semgrep:develop`  | [![semgrep-rules-test-develop](https://github.com/returntocorp/semgrep-rules/workflows/semgrep-develop/badge.svg)](https://github.com/returntocorp/semgrep-rules/actions?query=workflow%3Asemgrep-develop+branch%3Adevelop) |

Welcome! This repository is the “standard library” for [Semgrep](https://semgrep.dev) rules, but there are many more written by [r2c](https://r2c.dev) and other contributors available in the [Semgrep Registry](https://semgrep.dev/explore). If there a specific rule you are looking for, you can also search the Semgrep registry [here](https://semgrep.dev/r).

## How do I use these rules?

We recommend starting with `semgrep --config auto`. The `--config auto` flag will fetch rules relevant to your project from [Semgrep Registry](https://semgrep.dev/explore). The name of your project will be sent to Semgrep Registry as an identifier to make selecting relevant rules fast next time; source code will not be uploaded.

Alternatively, you can start with a pre-selected subset of rules that has already been carefully tuned for precision. These subsets of rules, which we call rulesets, may include rules not present in this repository. However, they are available for free on the [Semgrep Registry](https://semgrep.dev/explore). These rules have been written by open-source contributors and r2c.

If you are determined to drink from the firehose, you can also pull directly from the registry by specifying `r/<foldername.subfolder.etc>`. So to run all the Python Flask rules from the python/flask directory in this repo, just run:<br/>
`semgrep --config=r/python.flask`

Semgrep releases [new versions very frequently](https://github.com/returntocorp/semgrep/releases) and the rules in this repo are always updated to take advantage of new features or fix breaking changes on new releases. For that reason, we suggest that you avoid stale copies of registry rules.

## Contributing

We welcome Semgrep rule contributions directly to this repository! Since this repo is maintained by r2c, there are some extra benefits-for example, if there are bug reports for your rule, we’ll take responsibility to help fix it. If you are submitting to the semgrep-rules repo (rather than your own, separate repository as mentioned above) we’ll ask you to make r2c a joint owner of your contributions. While you still own copyright rights to your rule, joint ownership allows r2c to license these contributions to other [Semgrep Registry](https://semgrep.dev/r) users pursuant to the LGPL 2.1 under the [Commons Clause](https://commonsclause.com/). Check out the [Contributing Guidelines](/CONTRIBUTING.md) to get started.

You can also contact us at support@r2c.dev to make Semgrep rule contributions. We will import your rules for everyone to use!

### Rulesets

Rulesets -- combined sets of rules from the Semgrep registry -- are organized in a private repository. If you want to modify existing sets or create your own, please contact us at support@r2c.dev.

If you have more questions, please see the [FAQ section in the Semgrep docs](https://semgrep.dev/docs/faq).

## Help

Join [Slack](https://r2c.dev/slack) for the fastest answers to your questions! Or contact the team at [support@r2c.dev](mailto:support@r2c.dev).

### Rule Namespacing

The namespacing format for contributing rules is `<language>.<framework>.<category>.$MORE`. If a `framework` isn't applicable, use `lang` instead.

`category` is one of:
- security
- correctness
- best-practice
- maintainability
- performance

If a `security` rule is discouraging the use of a bad pattern (such as formatted SQL strings), we recommended appending `audit` to your namespace. This distinguishes it from a `security` rule that is specifically aiming to detect a vulnerability.

<p align="center">
    <img src="https://web-assets.r2c.dev/semgrep-live-namespacing.png" alt="semgrep.live rule namespace" width="500" />
</p>

### Github Action To Run Tests

If you fork this repo or create your own, you can add a special [semgrep-rules-test](https://github.com/marketplace/actions/semgrep-rules-test) Github Action to your workflow that will automatically test your rules by running `make test` using the latest version of semgrep.

See ours [here](.github/workflows/semgrep-rules-test.yml)

### Benchmarks
The [benchmark job](https://github.com/returntocorp/semgrep-rules/actions?query=workflow%3Arule-benchmarks) runs every weekend. It uploads a few artifacts, which can be downloaded. If you download the test logs, there are two relevant pieces of information in there: the benchmark table, which roughly shows the performance of every rule that completes in under 60 seconds, and any failed tests are rules that did not complete within 60 seconds.

To run benchmark tests locally, do the following from the root of `semgrep-rules`:
```
pipenv shell
pipenv install --dev
export PYTHONPATH=.
pytest --timeout=60 --rule-directory=[path_to_rule_directory] --git-repo=[git_URL] tests/performance/test_public_repos.py
```
If you omit `--git-repo` from the pytest command, it will run the provided benchmark repo.
