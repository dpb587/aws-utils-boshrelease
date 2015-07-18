# aws-utils-boshrelease

Some AWS-specific jobs and packages for BOSH deployments.

    releases:
      - name: "aws-utils"
        version: "latest"

Currently just the start of a proof of concept...


## Spot Termination Notice

Sometimes it's nicer to give the services running on your AWS Spot Instances a heads up that they're about to be
terminated, allowing them some time to gracefully leave clusters, rebalance, or offload state.

    jobs:
      - name: "example"
        templates:
          - release: "aws-utils"
            name: "spot-termination-notice"    
    properties:
      spot_termination_notice:
        scripts:
          - "/var/vcap/packages/consul/bin/consul maint -enable -reason 'Scheduled spot termination'"


## License

[Apache License 2.0](./LICENSE)
