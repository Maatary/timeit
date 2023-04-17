# Overview

This is a fork of the original [TimeIt project](https://github.com/merijn/timeit). It was forked as part of an [introductory](https://github.com/Maatary/haskell-no-project) work on how to use dependencies in haskell project without resorting to packaging.

# Notes

For the sake of being able to work with the project in Vscode using the LHS extension for Vscode, a hie.yaml file was added following the guideline provided in [hie-bios - Cabal](https://github.com/haskell/hie-bios/blob/master/README.md#cabal). 

Although cabal is referenced here, the goal was not to work with packaging per say but to allow VsCode to open the project and provide assistance. That is, LHS for VsCode requires either Cabal or Stack. As the original project had a cabal file, we just used it by configuring the Vscode to work with it trough an hie file, because the cabal syntax is from a cabal version that is too old (Otherwise VsCode would have handle the cabal file automatically). If we wanted to use stack, then we would have to use [hpack-convert](https://github.com/yamadapc/hpack-convert) to convert the cabal file to stack package.


## HLS for VsCode

- [The The Haskell Language Server](https://haskell-language-server.readthedocs.io/en/latest/) which enables Haskell in VsCode.

- Why HLS for Vscode does not always automatically pickup the cabal project is explained in [hie-bios#cabal](https://github.com/haskell/hie-bios#cabal), while the underlying mechanism that it relies upon is outlined in [implicit-configuration](https://github.com/haskell/hie-bios#implicit-configuration)
  
- The Official guideline to set up HLS for VsCode can be found in [configuring-your-project-build](https://haskell-language-server.readthedocs.io/en/latest/configuration.html#configuring-your-project-build)
  
- A Way to generate the hie.yaml file automatically for HLS for VsCode works with the project automatically[implicit-hie](https://github.com/Avi-D-coder/implicit-hie)

- Other links:

  - https://cabal.readthedocs.io/en/3.10/nix-local-build.html#developing-multiple-packages
  - https://stackoverflow.com/questions/71137389/how-to-create-cabal-project-file
  - https://theblogreaders.com/visual-studio-code-tips-reload-restart-visual-studio-code-window/
