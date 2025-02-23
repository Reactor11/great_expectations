---
title: How to initialize a Filesystem Data Context in Python
tag: [how-to, setup]
keywords: [Great Expectations, Data Context, Filesystem]

---

import TechnicalTag from '/docs/term_tags/_tag.mdx';
import Prerequisites from '/docs/components/_prerequisites.jsx'

<!-- ### 1. Import Great Expectations -->
import GxImport from '/docs/components/setup/python_environment/_gx_import.md'

<!--- ### 2. Verify the content of the Data Context -->
import DataContextVerifyContents from '/docs/components/setup/data_context/_data_context_verify_contents.md'

## Introduction

A <TechnicalTag tag="data_context" text="Data Context" /> will be required in almost all Python scripts utilizing GX, and will be implemented behind the scenes when using GX's <TechnicalTag tag="cli" text="CLI" />.

This guide will demonstrate how to initialize, instantiate, and verify the contents of a Filesystem Data Context from through Python code.

## Prerequisites

<Prerequisites requirePython = {false} requireInstallation = {true} requireDataContext = {false} requireSourceData = {null} requireDatasource = {false} requireExpectationSuite = {false}>

- A passion for data quality

</Prerequisites>

## Steps

### 1. Import Great Expectations

<GxImport />

### 2. Determine the folder to initialize the Data Context in

For purposes of this example, we will assume that we have an empty folder to initialize our Filesystem Data Context in:

```python title="Python code"
path_to_empty_folder = '/my_gx_project/'
```

### 2. Run GX's `get_context(...)` method

We will provide our empty folder's path to the GX library's `get_context(...)` method as the `context_root_dir` parameter.  Because we are providing a path to an empty folder `get_context(...)` will initialize a Filesystem Data Context at that location.

For convenience, the `get_context(...)` method will then instantiate and return the newly initialized Data Context, which we can keep in a Python variable.

```python title="Python code"
context = gx.get_context(context_root_dir=path_to_empty_folder)
```

:::info What if the folder is not empty?
If the `context_root_dir` provided to the `get_context(...)` method points to a folder that does not already have a Data Context present, the `get_context(...)` method will initialize a Filesystem Data Context at that location even if other files and folders are present.  This allows you to easily initialize a Filesystem Data Context in a folder that contains your source data or other project related contents.

If a Data Context already exists at the provided `path`, the `get_context(...)` method will not re-initialize it.  Instead, `get_context(...)` will simply instantiate and return the existing Data Context as is.
:::


### 3. Verify the content of the returned Data Context

<DataContextVerifyContents />

## Next steps

For guidance on further customizing your Data Context's configurations for <TechnicalTag tag="store" text="Metadata Stores" /> and <TechnicalTag tag="data_docs" text="Data Docs" />, please see:
- [How to configure an Expectation Store on a filesystem](docs/guides/setup/configuring_metadata_stores/how_to_configure_an_expectation_store_on_a_filesystem.md)
- [How to configure a Validation Result Store on a filesystem](docs/guides/setup/configuring_metadata_stores/how_to_configure_a_validation_result_store_on_a_filesystem.md)
- [How to configure and use a Metric Store](docs/guides/setup/configuring_metadata_stores/how_to_configure_a_metricsstore.md)
- [How to host and share Data Docs on a filesystem](docs/guides/setup/configuring_data_docs/how_to_host_and_share_data_docs_on_a_filesystem.md)

If you are content with the default configuration of your Data Context, you can move on to connecting GX to your source data:
- [How to configure a Pandas Datasource](docs/guides/connecting_to_your_data/datasource_configuration/how_to_configure_a_pandas_datasource.md)
- [How to configure a Spark Datasource](docs/guides/connecting_to_your_data/datasource_configuration/how_to_configure_a_spark_datasource.md)
- [How to configure a SQL Datasource](docs/guides/connecting_to_your_data/datasource_configuration/how_to_configure_a_sql_datasource.md)

## Additional information

### Related guides

To initialize a Filesystem Data Context from the terminal, please see:
- [How to initialize a new Data Context with the CLI](docs/guides/setup/configuring_data_contexts/how_to_configure_a_new_data_context_with_the_cli.md)

<!-- TODO
To instantiate an existing Data Context, reference:
- How to quickly instantiate a Data Context
- How to instantiate a specific Filesystem Data Context

To initialize and instantiate a temporary Data Context, see:
- How to explicitly instantiate an in-memory Ephemeral Data Context
-->

<!-- TODO
### Code examples

To see the full source code used for the examples in this guide, please reference the following scripts in our GitHub repository:
- [script_name.py](https://path/to/the/script/on/github.com)
-->