# App Engine Environments

**Standard**: Applications run in language specific sandboxes

- Complete isolation from OS/Disk/Other Apps
- `V1`: Java, Python, Go (Old versions)
  - Only for Python and PHP Runtimes
    - Restricted network Access
    - Only white-listed extensions and libraries are allowed
  - No restrictions for Java and Go runtimes
- `V2`: Java, Python, PHP, Node.js, Ruby, Go (Newer versions)
  - Full Network Access and No restrictions on Language Extensions

**Flexible**: Application instances run within Docker containers

- Makes use of Compute Engine virtual machines
- Support ANY runtime (with built-in support for Python, Java, Node.js, Go, Ruby, PHP, .NET)
- Provides access to background processes and local disks
