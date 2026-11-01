# Hugo Blog

Static blog built with [Hugo](https://gohugo.io) and the [Blowfish](https://github.com/nunocoracao/blowfish) theme, deployed to S3 + CloudFront via a GitHub workflow. Currently serves [blog.kyrylenko.ca](https://blog.kyrylenko.ca); also doubles as a template — fork it and update the config.

## Visual identity

The site intentionally matches [resume.kyrylenko.ca](https://resume.kyrylenko.ca) ([vlkyrylenko/resume](https://github.com/vlkyrylenko/resume)): same paper/ink/sage/coral palette, DM Sans / DM Mono / Instrument Serif type, Blowfish **v2.80.0** and Hugo **0.139.0** pins. The shared tokens live in `assets/css/custom.css` — if you change them on one site, mirror the change on the other.

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
5. Hugo version is pinned to `0.139.0` directly in the workflow (Blowfish v2.80.0 compat ceiling); no `HUGO_VERSION` variable needed.
6. Create a first PR to trigger the deployment workflow or follow the steps below to deploy locally.
   1. Create a `.aws/credentials` file by running `aws configure` and entering the access key and secret.
   2. Initialize git repository by running `git init`.
   3. Initialize the submodule by running `git submodule update --init --recursive`.
   4. Install hugo modules by running `hugo mod get -u`.
   5. Build the website by running `hugo`.
   6. Run a local server by running `hugo server -D`.
   7. (Optional) Deploy the website by running `hugo deploy`.