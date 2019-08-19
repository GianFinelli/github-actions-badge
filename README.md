DEPRECATED!! Instead of using this repository, you should put the following into your README which is supported directly by GitHub:

```
[![Actions Status](https://github.com/{owner}/{repo}/workflows/{workflow_name}/badge.svg)](https://github.com/{owner}/{repo}/actions)
```

# github-actions-badge

This is a small AWS lambda that renders a README badge based on the status of your Github Actions workflow. You can add the badge to your README by including:

```
[![Actions Status](https://xxx.execute-api.us-west-2.amazonaws.com/production/badge/{owner}/{repo})](https://xxx.execute-api.us-west-2.amazonaws.com/production/results/{owner}/{repo})
```

where `{owner}` and `{repo}` are replaced by the github username and the repository name, respectively. For example, this repository would use:

```
https://xxx.execute-api.us-west-2.amazonaws.com/production/badge/CultureHQ/github-actions-badge
```

Optionally a branch can be specified using the `branch` query parameter.
Without this parameter, it will use the `master` branch.

```
https://xxx.execute-api.us-west-2.amazonaws.com/production/badge/{owner}/{repo}?branch={branch}
```

The badge variants look like:

- ![Error](https://img.shields.io/badge/GitHub_Actions-error-red.svg?logo=github&logoColor=white)
- ![Failure](https://img.shields.io/badge/GitHub_Actions-failure-critical.svg?logo=github&logoColor=white)
- ![Pending](https://img.shields.io/badge/GitHub_Actions-pending-yellow.svg?logo=github&logoColor=white)
- ![Success](https://img.shields.io/badge/GitHub_Actions-success-success.svg?logo=github&logoColor=white)
- ![No Runs](https://img.shields.io/badge/GitHub_Actions-no_runs-lightgrey.svg?logo=github&logoColor=white)

## Options

You can pass additional options to the badge through the image URL that will be forwarded on to [shields.io](https://shields.io/#/) (the source for the images). The options are documented on their page.

For instance, if you wanted to change the style to `flat-square`, you could pass it as a query param as in:

```
[![Actions Status](https://xxx.execute-api.us-west-2.amazonaws.com/production/badge/{owner}/{repo}?style=flat-square)](https://xxx.execute-api.us-west-2.amazonaws.com/production/results/{owner}/{repo})
```

## Private repositories

In order for the lambda to get status from Github for private repos, you have to create
a token with repo access and set that in `.env.yml`.

```shell
cp .env.yml.example .env.yml
```

## Development

To develop locally, install dependencies with `yarn`. Then you can run `yarn start` at the root of the repository to start a local server. To deploy to your AWS environment, run `yarn deploy`.

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/CultureHQ/github-actions-badge.

## License

The code is available as open source under the terms of the [MIT License](https://opensource.org/licenses/MIT).
