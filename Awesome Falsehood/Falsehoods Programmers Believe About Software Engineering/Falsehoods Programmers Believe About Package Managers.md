# Falsehoods Programmers Believe About Package Managers
Creado: 2022-06-21 18:03
Tags: #every-programmer-should-know, #falsehoods, #software-engineering
Topic: [[Falsehoods Programmers Believe About Software Engineering]]

----

### Packages
---
1. A package has a name.
2. A package has only one name (see [#26](https://github.com/kdeldycke/meta-package-manager/issues/26)).
3. A package name is unique.
4. Package [names are composed of ASCII characters](https://github.com/kdeldycke/meta-package-manager/blob/v2.2.0/meta_package_manager/managers/homebrew.py#L205-L206).
5. A package name is the same as its ID (see [#11](https://github.com/kdeldycke/meta-package-manager/issues/11)).
6. There is only one way to install a package.
7. Only one version of a package is available on a system.
8. Package [upgrades can be automated](https://en.wikipedia.org/wiki/Dependency_hell).
9. All [packages have a version](https://github.com/kdeldycke/meta-package-manager/blob/v2.2.0/meta_package_manager/managers/mas.py#L71-L75).
10. [Versionned packages are immutable](https://github.com/kdeldycke/meta-package-manager/blob/v2.2.0/meta_package_manager/managers/homebrew.py#L230-L231).
11. Packages can’t upgrade themselves.
12. A package can be reinstalled.

### Package managers
---
1. Package managers provides the latest version of packages.
2. Package managers provides clean packages.
3. Package managers provides stable softwares.
4. Only [one instance of a package manager exist on the system](https://github.com/kdeldycke/meta-package-manager/blob/v2.2.0/meta_package_manager/managers/gem.py#L47-L51).
5. You can downgrade packages.
6. A package manager [can update itself](https://twitter.com/kdeldycke/status/772832404960636928).
7. A package is found under the same name in different package managers.
8. Package managers [can resolve dependencies](https://github.com/pypa/pip/issues/988).
9. All dependencies are provided by the package manager.
10. Package managers have a CLI.
11. Package managers behave the same across OSes and distributions.
12. Package managers [tracks installed versions](https://github.com/kdeldycke/meta-package-manager/blob/v2.2.0/meta_package_manager/managers/homebrew.py#L219-L221).
13. Package managers [can track removed packages](https://github.com/kdeldycke/meta-package-manager/blob/v2.2.0/meta_package_manager/managers/homebrew.py#L239-L242) (see [#17](https://github.com/kdeldycke/meta-package-manager/issues/17)).
14. Package managers are documented.
15. A package manager has a version.
16. A package manager check package integrity.
17. Package managers are secure.
18. Package managers can be unittested.
19. Package managers [can upgrade all outdated packages](https://github.com/kdeldycke/meta-package-manager/blob/v2.2.0/meta_package_manager/managers/pip.py#L94-L97).
20. Package managers are forbidden to upgrade other package managers.
21. Packages are only managed by one package manager.
22. Installing a package doesn’t require a reboot.
23. Package manager [output is consistent](https://github.com/kdeldycke/meta-package-manager/blob/v2.2.0/meta_package_manager/managers/mas.py#L42-L44).
24. A package manager can upgrade a package installed by the user.
25. All [users on the system have access to the package manager](https://github.com/kdeldycke/meta-package-manager/blob/v2.2.0/meta_package_manager/managers/gem.py#L95-L100).
26. Package managers do not remove user data.
27. Package managers [can bootstrap themselves](https://github.com/Homebrew/brew/blob/master/docs/Common-Issues.md#brew-complains-about-absence-of-command-line-tools).
28. Package managers supports multiple architectures.
29. You [only need one package manager](https://utcc.utoronto.ca/~cks/space/blog/tech/PackageManagersTwoTypes).

### Meta
---
- Implementing a meta package manager [is not a futile pursuit](https://xkcd.com/1654/).


## Referencias