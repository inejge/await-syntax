# Variants of `await` syntax for Rust

As the drive for async/await stabilization in Rust enters its final stretch,
the latest [discussion of await syntax](https://internals.rust-lang.org/t/await-syntax-discussion-summary/9914)
has shown that the issue is as contentious as ever, with several firmly
established camps. The lang team's excellent [write up](https://paper.dropbox.com/doc/Await-Syntax-Write-Up-t9NlOSeI4RQ8AINsaSSyJ)
has narrowed down the choices to "prefix" and "postfix" categories, each of
which contains several possible solutions, but so far the team hasn't reached
consensus.

While there have been commendable attempts to [illustrate the syntax](https://github.com/rust-lang/rust/issues/57640#issuecomment-455846086)
with more substantial code excerpts, in general I feel that the discussion
has been rather light on concrete, in-context examples. Even if a certain
amount of abstractness is inevitable, in this case there is an existing
corpus of working async code which can be adapted to various proposed
syntaxes without much difficulty: components of Google's Fuchsia OS written
in Rust.

I believe that there is value in seeing a language construct in the context
of the rest of the source code. This repo starts with the source of an
async-heavy utility and translates it to four variant syntaxes proposed by
the lang team. More source files and await syntaxes can be added if there's
interest: see the __Contributing__ section.

## Organization of the repo

The original source is copied from the tree at the commit `66e1924` of the
`master` branch of the Fuchsia [Garnet](https://fuchsia.googlesource.com/garnet/)
repo. This source uses the unstable `await!` macro. Translations to other
syntaxes are in separate branches, named after the proposals in the lang team
writeup:

* `prefix-mandatory`: Prefix await with mandatory delimiters.

* `prefix-sugar`: Prefix syntactic sugar for await+try.

* `postfix-field`: Postfix field access syntax.

* `postfix-method`: Postfix method syntax.

(The order of syntaxes in the above list follows the order in the writeup.)

## Contributing

If you notice an error in a translation, create a PR against the branch of the
translation.

If you want to add a source file with at least two translations, first create
a PR with the original against `master`, then the PRs for each translation
against the corresponding branch. The original should be from the tree
referenced in the __Organization__ section.

If you want to contribute a translation to another syntax, open an issue and
propose the creation of the appropriate branch. To keep the repo focused,
please don't propose syntaxes which aren't in the lang team's writeup. Then,
create a PR against the new branch.

## License

The contents of this repo is covered by Google's Fuchsia license, which can
be found in the LICENSE file.
