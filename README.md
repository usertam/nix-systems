# Externally extensible flake systems

Loosely based on [nix-systems/default](https://github.com/nix-systems/default), without `import`. See [nix-systems](https://github.com/nix-systems/nix-systems) for the pattern explanation.

## List of systems
- aarch64-darwin
- aarch64-linux
- x86_64-darwin
- x86_64-linux
- riscv64-linux

## Usage
```nix
{
  inputs = {
    nixpkgs.url = "github:NixOS/nixpkgs/nixpkgs-unstable";
    systems.url = "github:usertam/nix-systems";
  };

  outputs = { self, nixpkgs, systems }: {
    packages = nixpkgs.lib.genAttrs systems.systems (system: {
      default = nixpkgs.legacyPackages.${system}.hello;
    });
  };
}
```
