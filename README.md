# Hugo Blog

This is a template repository for Hugo website with a GitHub workflow to deploy the website to an S3 bucket & Cloudfront.

## How To

1. Create a new repository from this template.
2. Update the `hugo.toml` file in `config/default`.
   - Update the `baseURL` to your domain.
   - Update the `title` and `theme` if needed.
   - Update S3 `URL` and `CloudfrontId` if deploying to AWS. See the terraform module for more details.
3. Install dependencies:
   - node.js
   - nvm (for managing node versions)
   - [Golang](https://go.dev/doc/install)
   - [hugo](https://gohugo.io/installation/) (extended with deploy!)
   - [blowfish](https://blowfish.page/docs/getting-started/)
   - [AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)
4. Create an IAM access key and secret for the `publish` IAM user as well as preferred AWS region and store them in GitHub secrets.
   - `AWS_ACCESS_KEY_ID`
   - `AWS_SECRET_ACCESS_KEY`
   - `AWS_REGION`
5. Create a new GitHub variable for the `HUGO_VERSION` to specify the version of Hugo to use.
6. Create a first PR to trigger the deployment workflow or follow the steps below to deploy locally.
   1. Create a `.aws/credentials` file by running `aws configure` and entering the access key and secret.
   2. Initialize git repository by running `git init`.
   3. Initialize the submodule by running `git submodule update --init --recursive`.
   4. Install hugo modules by running `hugo mod get -u`.
   5. Build the website by running `hugo`.
   6. Run a local server by running `hugo server -D`.
   7. (Optional) Deploy the website by running `hugo deploy`.