## Forgejo runner registration

The runner needs a UUID and token that Forgejo already knows about, so create the runner in Forgejo first, then give the credentials to the pod.

### 1. Create the runner in Forgejo

1. Open the runners page for the scope you want:
    - Instance-wide: `/admin/actions/runners`
    - Organization: `/org/<org>/settings/actions/runners`
    - User: `/user/settings/actions/runners`
    - Single repo: `/<owner>/<repo>/settings/actions/runners`
2. Click **Create new runner**, enter a name, and click **Create**.
3. Copy the **UUID** and **token**. The token is only shown once.

### 2. Store the credentials

Save them in the secret manager that feeds the ExternalSecret, under these keys:

| Key     | Value                      |
| ------- | -------------------------- |
| `uuid`  | The full 36-character UUID |
| `token` | The token exactly as shown |

The runner pod mounts them at `/etc/forgejo-runner-secret/uuid` and `/etc/forgejo-runner-secret/token`.
