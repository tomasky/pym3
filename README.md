# `p`

## Python Version Management, Simplified.

![introduction](https://cloud.githubusercontent.com/assets/1139621/7488032/37f37308-f389-11e4-8995-89f7cba5ad8b.gif)

`p` is **powerful** and **feature-packed**, yet **simple**; both in setup and use. There are no tricky settings, options, or crazy dependencies. `p` is just a helpful ~600 line Bash script that gets the job done.

**`p` let's you quickly switch between Python versions whenever you need to, removing the barrier between Python 2.x.x and 3.x.x.**

`p` was heavily inspired by [`n`, a version manager for Node.js](https://github.com/tj/n).

`p` is also great for getting started using Python development versions. Use `p latest` to get up and running with the latest development version of Python!

## Getting Started

After the [super painless drag-and-drop installation](#installation), you can [start using `p`](#usage) right away.

## Usage

```
Usage: p [COMMAND] [args]

Commands:

p                              Output versions installed
p status                       Output current status
p <version>                    Activate to Python <version>
	p latest                     Activate to the latest Python release
	p stable                     Activate to the latest stable Python release
p use <version> [args ...]     Execute Python <version> with [args ...]
p bin <version>                Output bin path for <version>
p rm <version ...>             Remove the given version(s)
p prev                         Revert to the previously activated version
p default                      Revert to the system default python version
p ensurepath                   Add python path to your search path
p unpkg <pkg ...>              Remove the given name(s) pip packages and unused dependencies
p shell                        Add python bin path to a new bash shell
p p                            Wrapper pip command
p px                           Wrapper pipx command
p py                           Wrapper poetry command
p up                           Update all pipx libs,Wrapper pipdate command,update all pip packages
p migrate <ver1> <ver2>        Migrate pip package from a Python version to another
p ls                           Output the versions of Python available
	p ls latest                  Output the latest Python version available
	p ls stable                  Output the latest stable Python version available

Options:

-V, --version   Output current version of p
-h, --help      Display help information

Environment variables:

P_PREFIX        Python versions installation dir ,default: ~/.local
PY_INSTALL_FLAG Python installation configure flags, eg: --enable-optimizations
```

## Installation Python dependencies

Ubuntu/Debian:

```sh
sudo apt-get install -y build-essential zlib1g-dev
curl -o /tmp/openssl.tar.gz https://www.openssl.org/source/openssl-1.1.1n.tar.gz
cd /tmp && tar xvf openssl* && cd openssl-*
./config && make -j 8 && sudo make install
echo -e "/usr/local/lib64" >> /etc/ld.so.conf.d/ssl.conf
sudo ldconfig
```

Centos:

```sh
sudo yum install -y xz-devel sqlite-devel libffi-devel zlib-devel openssl11-libs
# install openssl11-libs or upgrade openssl to 111n
curl -o /tmp/openssl.tar.gz https://www.openssl.org/source/openssl-1.1.1n.tar.gz
cd /tmp && tar xvf openssl* && cd openssl-*
./config && make -j 8 && sudo make install
echo -e "/usr/local/lib64"  >> /etc/ld.so.conf.d/ssl.conf
sudo ldconfig
```

## Installation

After downloading the Bash script, simply copy it over to your `$PATH` and `p` will take care of the rest.

```sh
$ curl -o p https://raw.githubusercontent.com/tomasky/pym3/master/bin/p
$ chmod +x p
$ mv p /usr/local/bin
```

Alternatively, you can install `p` via `npm`:

```shell
npm install -g pym3
```

So far, `p` has only been tested in Bash. If you can make `p` work on another shell, please send in a pull request!

Set `python` versions installation dir:

```shell
# default is `~/.local`
# add this to .bashrc
export P_PREFIX=/usr/local
```

Set `python` download mirror:

```shell
# add this to .bashrc
export PYTHON_MIRROR=https://mirrors.huaweicloud.com/python/
```

## Updating

Simply follow the above steps and swap out the old Bash script with the new one!

## Contributing

Contributions are always welcome.

Find something interesting in the TODO below, fork our code, create a new branch, and send us a pull request.

There are only two rules: avoid [code smells](http://blog.codinghorror.com/code-smells/) and abide by the syntax-formatting of the existing code.

## TODO

- **greater abstraction between Python 2.x.x and 3.x.x**
- per-directory/project Python version
- **also manage PyPy**

## FAQs

- How does `p` differ from [`pyenv`](https://github.com/yyuu/pyenv)?
  - `p` is designed for the average Python user. You can get up and running with the latest development build of Python with one simple command: `p latest`. No configuration is necessary; `p` manages everything for you.
  - On the other hand, `pyenv` is for the more advanced user who is comfortable configuring their Python environment to all their needs. `p` provides the basics in one easy to use aesthetically-pleasing command.
  - Additionally, `p` is easier to use. To switch your Python version, simply run `p` and you'll be presented with a list of installed Python versions to select from that you can scroll through with your arrow keys and select with the return key.
  - `p` is great at dealing with any version of Python. If it's not installed, running `p <version>` will download the source, configure it for your system, and compile it, all in one simple command.
- How does `p` work?
  - `p` stores each Python version installed in `/usr/local/p/versions/python`. When a Python version is activated, `p` creates a symbolic link to the Python binary located at `/usr/local/p/versions/python/python`. Since `p` prefixes the $PATH with `/usr/local/p/versions/python`, this version of `python` is found first; hence, it is used over the default version of Python installed on your system.
- How do I revert back to my default Python version?
  - Simply run `p default` and `p` will remove the symbolic link described above; therefore reverting back to your default Python version.
- Does `p` download the source each time I activate or install a version?
  - Nope. `p` stores the source for each of the versions installed, allowing for quick activations between already-installed versions.
- How do I get this working on Windows?
  - Unfortunately, `p` is not supported on Windows at the time. If you know of a workaround, send in a pull request!

## License

The below license was included in [`n`](https://github.com/tj/n) and is included below. `p`'s license (also MIT) can be found in [the LICENSE file](https://github.com/qw3rtman/p/blob/master/LICENSE).

> (The MIT License)

> Copyright (c) 2014 TJ Holowaychuk &lt;tj@vision-media.ca&gt;

> Permission is hereby granted, free of charge, to any person obtaining
> a copy of this software and associated documentation files (the
> 'Software'), to deal in the Software without restriction, including
> without limitation the rights to use, copy, modify, merge, publish,
> distribute, sublicense, and/or sell copies of the Software, and to
> permit persons to whom the Software is furnished to do so, subject to
> the following conditions:

> The above copyright notice and this permission notice shall be
> included in all copies or substantial portions of the Software.

> THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND,
> EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
> MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
> IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
> CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
> TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
> SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
