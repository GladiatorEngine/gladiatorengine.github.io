---
sort: 1
---

# Installation

The easiest way to install and start using GladiatorEngine is [Homebrew](https://brew.sh).

## Installation with Homebrew

To install GladiatorEngine with Homebrew you just need to install GladiatorEngine toolset:
```shell
brew install GladiatorEngine/tap/gladiator-tools
```
## Project integration
### Recommended
Use GladiatorEngine toolset to create new Xcode project:
```shell
gladiator-engine project new TechnologyDemo
```
### Non-recommended
Add GladiatorEngine to your Package.swift or Xcode Project as a dependency:
```swift
// swift-tools-version:5.3
// The swift-tools-version declares the minimum version of Swift required to build this package.

import PackageDescription

let package = Package(
    name: "technology-demo",
    platforms: [
        .macOS(.v10_15)
    ],
    dependencies: [
        // Dependencies declare other packages that this package depends on.
        // .package(url: /* package url */, from: "1.0.0"),
        .package(url: "https://github.com/GladiatorEngine/GladiatorEngine", .branch("main")),
    ],
    targets: [
        // Targets are the basic building blocks of a package. A target can define a module or a test suite.
        // Targets can depend on other targets in this package, and on products in packages this package depends on.
        .target(
            name: "technology-demo",
            dependencies: [
                .product(name: "GladiatorEngine", package: "GladiatorEngine")
            ]),
        .testTarget(
            name: "TechnologyDemoTests",
            dependencies: ["technology-demo"]),
    ]
)
```
