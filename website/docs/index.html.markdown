---
layout: "veeam"
page_title: "Provider: veeam"
sidebar_current: "docs-veeam-index"
description: |-
  The Veeam provider is used to interact with the resources supported by
  Veeam server. The provider needs to be configured with the proper credentials
  before it can be used.
---

# Veeam Provider

The Veeam provider is used to interact with the resources supported by
Veeam.
The provider needs to be configured with the proper credentials before it can be used.

Use the navigation to the left to read about the available resources.

~> **NOTE:** The Veeam Provider currently represents _initial support_
and therefore may undergo significant changes as the community improves it. This
provider at this time only supports adding virtual machine resource.

## Example Usage

```hcl
# Configure the Veeam Provider
provider "veeam" {
  server_ip = "${var.VEEAM_SERVER_IP}"
  port = ${var.VEEAM_SERVER_PORT}
  username = "${var.VEEAM_SERVER_USERNAME}"
  password = "${var.VEEAM_SERVER_PASSWORD}"
}

# Resource veeam_job_vm to add vm to the backup job in veeam server
resource  "veeam_job_vm" "addvm"{
    job_name = "${var.VEEAM_JOB_NAME}"
    vm_name = "${var.VEEAM_VM_NAME}"
}

```

## Argument Reference

The following arguments are used to configure the Veeam Provider:

* `user` - (Required) This is the username for Veeam Server operations. Can also
  be specified with the `VEEAM_SERVER_USERNAME` environment variable.
* `password` - (Required) This is the password for Veeam Server API operations. Can
  also be specified with the `VEEAM_SERVER_PASSWORD` environment variable.
* `ip` - (Required) This is the Veeam server ip.
  operations. Can also be specified with the `VEEAM_SERVER_IP` environment
  variable.
* `port` - (Required) This is the port number for http.

## Acceptance Tests

The Veeam provider's acceptance tests require the above provider
configuration fields to be set using the documented environment variables.

In addition, the following environment variables are used in tests, and must be
set to valid values for your Veeam Server environment:

 * VEEAM\_JOB\_NAME
 * VEEAM\_VM\_NAME

Once all these variables are in place, the tests can be run like this:

```
make testacc TEST=./builtin/providers/veeam
```
