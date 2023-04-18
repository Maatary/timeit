# Overview

This is a fork of the original [TimeIt project](https://github.com/merijn/timeit). It was forked as part of an [introductory](https://github.com/Maatary/haskell-no-project) work on how to use dependencies in haskell project without resorting to packaging.

# Notes

For the sake of being able to work with the project in Vscode using the LHS extension for Vscode, a hie.yaml file was added following the guideline provided in [hie-bios - Cabal](https://github.com/haskell/hie-bios/blob/master/README.md#cabal). 

Although cabal is referenced here, the goal was not to work with packaging per say but to allow VsCode to open the project and provide assistance. That is, LHS for VsCode requires either Cabal or Stack. As the original project had a cabal file, we just used it by configuring the Vscode to work with it trough an hie file, because the cabal syntax is from a cabal version that is too old (Otherwise VsCode would have handle the cabal file automatically). If we wanted to use stack, then we would have to use [hpack-convert](https://github.com/yamadapc/hpack-convert) to convert the cabal file to stack package.


## General Introduction to Haskell Language Server and VsCode.

- [The haskell-language-server (HLS) project](https://haskell-language-server.readthedocs.io/en/latest/what-is-hls.html) is an implementation of a server (a “language server”) for the Language Server Protocol (LSP). A language server talks to a client (typically an editor), which can ask the server to perform various operations, such as reporting errors or providing code completions. The advantage of this system is that clients and servers can interoperate more easily so long as they all speak the LSP protocol. In the case of HLS, that means that it can be used with many different editors, since editor support for the LSP protocol is now widespread.

- HLS is responsible for actually understanding your project and answering the questions that the client asks of it, such as: what completion items could go here? are there any errors in the project? and so on. 

- In order to actually use it a client is needed (editor). The client is responsible for managing your interaction with the server: launching it, dispatching commands to it, and displaying or implementing responses. Some clients will even install the server binaries for you, such is the case for VsCode.
  
- **HLS needs to know how to build your Haskell project**: what flags to pass, what packages to provide, etc. It gets this information from the build system used by your project (**typically cabal or stack**). The tool used to do this is called **hie-bios**. hie-bios calls the strategy it uses to get compilation flags (e.g. “ask cabal”) a **“cradle”**.
  

- For instance, if you delete timeit.cabal and start HLS for VsCode, everything will work. This is because the project has no dependency what so ever. So Likely LHS just rely on the global GHC current config and compile the project (see [How does Haskell language Server manage to work with a project with only standalone haskell file?](https://stackoverflow.com/questions/76039680/how-does-haskell-language-server-manage-to-work-with-a-project-with-only-standal?noredirect=1#comment134108822_76039680))

## HLS for VsCode

- [The The Haskell Language Server](https://haskell-language-server.readthedocs.io/en/latest/) which enables Haskell in VsCode.

- Why HLS for Vscode does not always automatically pickup the cabal project is explained in [hie-bios#cabal](https://github.com/haskell/hie-bios#cabal), while the underlying mechanism that it relies upon is outlined in [implicit-configuration](https://github.com/haskell/hie-bios#implicit-configuration)
  
- The Official guideline to set up HLS for VsCode can be found in [configuring-your-project-build](https://haskell-language-server.readthedocs.io/en/latest/configuration.html#configuring-your-project-build)
  
- A Way to generate the hie.yaml file automatically for HLS for VsCode works with the project automatically [implicit-hie](https://github.com/Avi-D-coder/implicit-hie)

- Other links:

  - https://cabal.readthedocs.io/en/3.10/nix-local-build.html#developing-multiple-packages
  - https://stackoverflow.com/questions/71137389/how-to-create-cabal-project-file
  - https://theblogreaders.com/visual-studio-code-tips-reload-restart-visual-studio-code-window/
