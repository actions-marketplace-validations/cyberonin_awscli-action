# awscli-action

Github Action for AWS Command Line Interface

## Example usage

```
name: S3 Sync

on:
	push:
		branches:
			- master

jobs:
	s3sync:
		runs-on:
		steps:
		- uses: actions/checkout@master
		- uses: cyberonin/awscli-action@master
			with:
			  args: s3 sync --acl public-read --follow-symlinks --delete ${SOURCE_DIR} s3://${AWS_S3_BUCKET}
			env:
			  AWS_DEFAULT_REGION: "us-east-1"
			  AWS_ACCESS_KEY_ID: ${{ secrets.AWS_ACCESS_KEY_ID }}
			  AWS_SECRET_ACCESS_KEY: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
			  AWS_S3_BUCKET: ${{ secrets.AWS_S3_BUCKET }}
			  SOURCE_DIR: 'build'

```

## Developement

It's best practice to also add a version tag for releases of your action. For more information on versioning your action, see "About actions."

```sh
git tag -a -m "My first action release" v1
git push --follow-tags
```
