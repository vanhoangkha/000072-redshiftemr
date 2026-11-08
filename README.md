# Analytics on AWS workshop

> Analytics with Amazon Redshift and Amazon EMR.

A hands-on workshop from the [AWS First Cloud Journey](https://github.com/vanhoangkha/aws-first-cloud-journey) series, available in English and Vietnamese.

**Read the workshop online:** https://vanhoangkha.github.io/000072-redshiftemr/

## Overview

Welcome to the Analytics workshop on AWS. The purpose of this workshop is to acquaint you with the different analytics services offered in the AWS Analytics portfolio

The workshop will cover various modules that discuss different aspects of constructing an analytics platform on AWS. Participants will acquire knowledge on data ingestion, storage, transformation, and utilization using various analytics services including AWS Glue, Amazon Athena, Amazon Kinesis, Amazon EMR, Amazon QuickSight, as well as AWS Lambda and Amazon Redshift. The architecture diagram below provides a more detailed representation of the design:

## Workshop contents

1. Introduction
2. Preparatory steps
3. Ingest and Store
   - Creating Kinesis Firehose
   - Generate Dummy Data
4. Catalog Data
   - Create IAM Role
   - Creating AWS Glue Crawlers
   - Verify newly created tables in catalog
5. Transform Data with AWS Glue (interactive sessions)
6. Transform Data with AWS Glue Studio (graphical interface)
7. Transform Data with AWS Glue DataBrew
8. Transform Data with EMR
9. Analysis with Athena
10. Analysis with Kinesis Data Analytics
11. Visualize in Quicksight
12. Serve with Lambda
13. Warehouse on Redshift
14. Clean up

## Prerequisites

- An AWS account with permissions to create the resources used in the labs
- Basic familiarity with the AWS Management Console
- [Hugo](https://gohugo.io/installation/) (extended edition) if you want to run the site locally

## Run locally

```bash
git clone --recurse-submodules https://github.com/vanhoangkha/000072-redshiftemr.git
cd 000072-redshiftemr
hugo server
```

Then open http://localhost:1313 in your browser.

## Repository structure

| Path | Purpose |
| --- | --- |
| `content/` | Workshop pages (`*.md` English, `*.vi.md` Vietnamese) |
| `static/` | Images and other static assets |
| `layouts/` | Hugo layout overrides |
| `themes/` | Hugo theme |
| `config.toml` | Site configuration |

## Cost and cleanup

The labs create AWS resources that may incur charges. Complete the **Clean up** chapter when you finish to remove them.

## Contributing

Contributions are welcome. See [CONTRIBUTING.md](CONTRIBUTING.md).

To report a security issue, see [SECURITY.md](SECURITY.md).

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE).
