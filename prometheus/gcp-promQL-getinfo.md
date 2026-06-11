```sql
max by (
  instance,
  node,
  store_name,
  model_name
) (
  node_cpu_info{store_name="example_name"}
)
* on(instance) group_left(mem_gb)
(
  node_memory_MemTotal_bytes{store_name="example_name"} / 1024^3
)
* on(instance) group_left(
    "bios_release",
    "bios_date",
    "bios_version",
    "board_name",
    "product_name",
    "product_serial",
    "product_version"
)
node_dmi_info
```
