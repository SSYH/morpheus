[![CircleCI](https://circleci.com/gh/benedekfazekas/morpheus.svg?style=svg)](https://circleci.com/gh/benedekfazekas/morpheus)
[![codecov](https://codecov.io/gh/benedekfazekas/morpheus/branch/master/graph/badge.svg)](https://codecov.io/gh/benedekfazekas/morpheus)

# Morpheus

Generate dependency graph(s) for variables in Clojure(Script) namespaces.

## Usage

Add an alias for `morpheus` in your deps.edn.

```clojure
{:aliases
  {:morpheus {:extra-deps {thomasa/morpheus {:git/url "https://github.com/benedekfazekas/morpheus.git"
                                             :sha "d3decebc1cb9ef697cd34781f9cf83d44a071e85"}}
              :main-opts ["-m" "thomasa.morpheus.main"]}}}
```

Run it in your project, provide directory to generate output files into -- directory needs to exist, format -- png, svg and dot is supported, latter is default -- and a list of paths to analyse.

Morpheus will generate a file per project variable with its dependency graph where nodes are other variables in the project or in one of the dependencies of the project.

```
clj -A:morpheus -d graphs -f png src test
```

For anything else than a dot file you need to graphiz installed. Alternatively you can use a viewer online, for example [edotor](https://edotor.net/).

If you generate svg format you can leverage the references added to the graph nodes: you can navigate to subgraphs in your dependency tree.

## Example

![mranderson.move__replace-in-import.svg](./mranderson.move__replace-in-import.svg)

Uses [clj-kondo](https://github.com/borkdude/clj-kondo) to analyse namespaces under provided paths.
