# disable-f5-pool-member

An action that will enable an F5 pool member in a specific pool.
  
## Inputs

| Parameter          | Is Required | Default | Description                                                                                                                                                                                            |
| ------------------ | ----------- | ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `ltm-host-name`    | true        | N/A     | The hostname of the Local Traffic Manager (LTM)                                                                                                                                                        |
| `ltm-username`     | true        | N/A     | Username of F5 LTM User                                                                                                                                                                                |
| `ltm-password`     | true        | N/A     | Password of F5 LTM User                                                                                                                                                                                |
| `ltm-pool-name`    | true        | N/A     | The pool to disable the member in                                                                                                                                                                      |
| `current-host`     | true        | N/A     | The hostname of the current machine being deployed                                                                                                                                                     |
| `max-wait-time`    | true        | 300     | Max Wait Time in seconds                                                                                                                                                                               |
| `connection-count` | true        | 0       | By default the action waits for no connections to be left on the node.  If a different threshold is specified, once the number of connections is reached, the API will kill the remaining connections. |

## Outputs
No Outputs

## Example

```yml
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: im-open/disable-f5-pool-member@v1.0.0
        with:
          ltm-host-name: 'devlb.mycompany.com'
          ltm-username: 'operator-svc-dev'
          ltm-password: ${{ secrets.F5_PASSWORD }}
          ltm-pool-name: '/Dev/api.dev.mycompany.com.https.443'
          current-host: 'waq2-abcd'
          max-wait-time:  120
          connection-count: 5
      
      - run: ./deploy.sh

```


## Code of Conduct

This project has adopted the [im-open's Code of Conduct](https://github.com/im-open/.github/blob/master/CODE_OF_CONDUCT.md).

## License

Copyright &copy; 2021, Extend Health, LLC. Code released under the [MIT license](LICENSE).
