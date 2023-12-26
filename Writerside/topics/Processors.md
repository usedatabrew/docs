# Processors

DataBrew has a concept of processors, where each one of them is an independent building block of the pipeline.
The processor takes a data frame (e.g., a single row from your database) and performs an operation.

The goal of using processors is to transform or enrich your data frame, so you will not have to worry about writing any
extra logic outside DataBrew cloud (or Blink if you are using an Open Source version)

We are constantly working on adding a new Processor to DataBrew. If you have a specific request - please, contact us
[contact@databrew.tech](mailto:contact@databrew.tech) and will try to do everything possible to bring your processor on
board.

| Processor name  | Available in Open Source | Details                                                                           | Stage   |
|-----------------|--------------------------|-----------------------------------------------------------------------------------|---------|
| Open AI ChatGPT | ✅                        | Sends your data frame to chat GTP and perform the operation you ask               | Ready   |
| SQL Filter      | ✅                        | Filters, selects only the needed data from your data frame                        | Ready   |
| HTTP Request    | ✅                        | Sends your data to HTTP endpoint so trigger custom actions, like webhooks         | Ready   |
| SQL Query       | ✅                        | Connects to SQL-compatible datasource to enrich your data to execute custom query | Planned |
| Email checker   | ✅                        | Extracts email from the data frame and check is it's suspicious                   | Planned |