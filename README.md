# composite-action-login-aws

This repository stores a [composite action](https://github.blog/changelog/2021-08-25-github-actions-reduce-duplication-with-action-composition/) used to set up aws login in order to release a helm chart using helmfile.

You can use this composite action as a step in your workflow like:
```
 - id: aws-login
        if: ${{ steps.set-cloud-info.outputs.result == 'aws' }}
        uses: prefapp/composite-action-login-aws@v1
        with:
            access-key: ${{ env.AWS_ACCESS_KEY }}
            secret-key: ${{ env.AWS_SECRET_KEY }}
            cluster-name: ${{ env.CLUSTER_NAME }}
            aws-region: ${{ env.AWS_REGION }}

# ${{ steps.aws-login.outputs.helmfile-creds }}
```