# Overview

This is a fork of the original [TimeIt project](https://github.com/merijn/timeit). It was forked as part of an [introductory](https://github.com/Maatary/haskell-no-project) work on how to use dependencies in haskell project without resorting to packaging.

# Notes

For the sake of being able to work with the project in Vscode using the LHS extension for Vscode, a hie.yaml file was added following the guideline provided in [hie-bios - Cabal](https://github.com/haskell/hie-bios/blob/master/README.md#cabal). 

Although cabal is referenced here, the goal was not to work with packaging per say but to allow VsCode to open the project and provide assistance. That is, LHS for VsCode requires either Cabal or Stack. As the original project had a cabal file, we just used it by configuring the Vscode to work with it trough an hie file, because the cabal syntax is from a cabal version that is too old (Otherwise VsCode would have handle the cabal file automatically). If we wanted to use stack, then we would have to use [hpack-convert](https://github.com/yamadapc/hpack-convert) to convert the cabal file to stack package.

