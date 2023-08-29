## Lab 3

Today we will learn the basics of scripts, as well as how to properly use an HPC. 

## Scripts

Scripts are the foundation of bioinformatics. They provide automation, flexibility, and speed in analyses--particularly tasks that are repeated over days, months, or years. Scripts can run a single command, or a hundred million (don't do this, that makes debugging impossible and you will hate your past self). Although in some cases it may be possible to run commands one by one, and in fact this can be really helpful for assembling pipelines/troubleshooting, it is not fun or feasible in most cases. 

Scripts add a lot of flexibility and speed. In Linux environments we use shell scripts, which typically end in `.sh` (but do not have to.

All scripts must start with a `shebang`. This is a weird term. Here is what Wikipedia says about it:

> The name shebang for the distinctive two characters may have come from an inexact contraction of SHArp bang or haSH bang, referring to the two typical Unix names for them. Another theory on the sh in shebang is that it is from the default shell sh, usually invoked with shebang.



```bash
#!/bin/bash
```
