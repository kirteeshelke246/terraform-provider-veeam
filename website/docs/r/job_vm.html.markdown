---
layout: "veeam"
page_title: "Veeam: veeam_job_vm"
sidebar_current: "docs-veeam-resource-inventory-folder"
description: |-
  Adds virtual machine to backup job in veeam server.
---

# veeam\_job\_vm

Adds virtual machine to backup job in veeam server.

## Example Usage

```hcl
resource "veeam_job_vm" "admins" {
  job_name        = "abcd"
  vm_name         = "wxyz"
}
```

## Argument Reference

The following arguments are supported:

* `job_name` - (Required) name of the backup job in veeam server .
* `vm_name` - (Required) name of the virtual machine to add to the backup job.

