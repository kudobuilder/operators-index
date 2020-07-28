# KUDO Operators Index

Index of the community operators for KUDO.

Each item in `operators` references one or more versions of an operator package. The community repository is build from the referenced packages. There's a one-to-one relationship between the referenced items in the index and the packages in the community repository.

## Operator References

As operators are developed in separate Git repositories, the operator package distributed in this repository are referenced for tagged versions. The Git repository is defined as a _source_, that is then used by the _git_ settings of a _version_.

```yaml
apiVersion: index.kudo.dev/v1alpha1
kind: Operator
name: My Operator
gitSources:
  - name: my-operator
    url: https://github.com/example/my-operator.git
versions:
  - operatorVersion: "1.1.0"
    git:
      source: my-operator
      directory: operator
      tag: v1.1.0
  - operatorVersion: "1.0.0"
    git:
      source: my-operator
      directory: operator
      tag: v1.0.0
```

Specific commits in a Git repository can be referenced by their SHA.

```yaml
versions:
  - operatorVersion: "1.2.0"
    git:
      source: my-operator
      directory: operator
      sha: 2b5b8ae28a83eb171d1c3094b92a1cc07e8c26f4

```

### Application Versions

In addition to the mandatory `operatorVersion` field, one can optionally set the `appVersion` field to the version of the application bundled by the operator.

```yaml
versions:
  - appVersion: "5.7"
    operatorVersion: "0.3.0"
```

### Referencing Tarballs

If one cannot reference a Git repository, a link to a tarball can be used instead.

```yaml
versions:
  - operatorVersion: "1.0.0"
    url: https://example.org/my-operator-1.0.0.tgz
```

## Current Limitations

* Operators and versions cannot be removed from the index yet
* Only operators compatible with the latest KUDO release can be added
