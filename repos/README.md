# About Repos

## `hurd`

Contains all git repos from official Hurd project. You can get information from
Hurd at <https://www.gnu.org/software/hurd/source_repositories.html>.

### `hurd/glic`

Because Hurd development uses topgit (you can build it follow [tools/topgit
section](#tools-topgit)). So it is very inconvenient to add it as a git
submodule.

So to init it, first [install topgit](#tools-topgit). you can run following
commands, which is described at
<https://www.gnu.org/software/hurd/source_repositories/glibc.html>.

```sh
cd repos/hurd && mkdir -p glibc && cd glibc
git init
git remote add savannah https://git.savannah.gnu.org/git/hurd/glibc.git
git remote update
tg remote --populate savannah

git checkout tschwinge/Roger_Whittaker
```

Now you get the real glibc code of Hurd.

## `tools`

Contains additional tools needed to build Hurd and maintain repos.

### `tools/topgit` {#tools-topgit}

Topgit upstream repo is at <https://github.com/greenrd/topgit>. However, it is
archived, so I download the last codes directly both to accelerate development
and to avoid the risk of deletion of upstream repo.

Unfortunately, topgit does not allow installation to paths rather than `/usr` or
`$HOME` including `/usr/local` because paths in scripts are hard-coded. When it
is installed to `$HOME`, the related paths would be the same as the ones in
`/usr`. So you will get `bin`s directory at `$HOME`. But this is the only way if
you don't want to pollute `/usr` in your system.

It is easy to build and install topgit.

```sh
cd repos/tools/topgit
make
make install # this will install to $HOME by default
```
