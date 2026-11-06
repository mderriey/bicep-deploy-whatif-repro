# azure/bicep-deploy what-if repro

Repro for [Azure/bicep-deploy#374](https://github.com/Azure/bicep-deploy/issues/374).

[`main.bicepparam`](main.bicepparam) sets an invalid storage account name, so ARM rejects the what-if with `InvalidTemplateDeployment` / `AccountNameInvalid`. `az deployment group what-if` with the same files fails too.

The [workflow](.github/workflows/what-if.yml) runs the same what-if with two versions of `azure/bicep-deploy`:

| Version | Result |
| --- | --- |
| v2.4.0 | The job passes and reports `Resource changes: no change.` |
| v2.5.0 | The job fails and shows the ARM error. |

See the [workflow runs](../../actions/workflows/what-if.yml).
