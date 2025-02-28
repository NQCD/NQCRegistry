This package registry contains all publicly released packages in the NQCD ecosystem. 

# How to update a package

Updating a package by merging into `main` on its respective repository isn't enough to trigger an update that is visible to Pkg, unless you have explicitly installed a package tracking its main branch by running `]install NQCDynamics.jl#main`. 
For an update to work, you need to `]install LocalRegistry` in the global project of your Julia installation. 

Clone the repository for the package you'd like to update and make sure you have NQCRegistry added to your Pkg registries. 
Make sure you have checked out the main branch, as you will register another branch on the Registry otherwise, which causes confusion. 

Once this is done, open a Julia REPL within the directory of the package you're updating and run:
```julia

using LocalRegistry
register()

```

LocalRegistry should update the version entry for the package automatically and might ask for git credentials along the way as it updates this repository. 

# How to register a package for the first time

The process for this is nearly identical to updating a package. Make sure your `origin` remote for the repository of the package you're registering for the first time is set to a HTTP URL, not an SSH path as this isn't supported by all Julia installations. 

Once you have made sure everything is properly set up, you can register a new package by opening a Julia REPL in the directory of your package:
```julia
using LocalRegistry
register(;registry = https://github.com/NQCD/NQCRegistry/NQCRegistry.git)
```

**If anything goes wrong, contact @alexsp32 for help.**
