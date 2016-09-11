## How to reproduce

**1.**

Clone the repo

```
git clone git@github.com:the-forks/bundler_test_case.git

cd bundler_test_case
```

### Positive case

**2.**

Uninstall all versons of Bundler in a current gemset

```
gem uninstall bundler

Continue with Uninstall? [yN] Y

Remove executables: bundle, bundler
in addition to the gem? [Yn] Y
```

**3.**

Install version of bundler that does the things right

```
gem install bundler -v=1.11.2
```

**4.**

Remove `Gemfile.lock`

```
rm -f Gemfile.lock
```

**5.**

Bundle it!

```
bundle

> Bundle complete! 2 Gemfile dependencies, 3 gems now installed.
> Use `bundle show [gemname]` to see where a bundled gem is installed.
```

It's ok!

### Negative case

**2.**

Uninstall all versons of Bundler in a current gemset

```
gem uninstall bundler

Continue with Uninstall? [yN] Y

Remove executables: bundle, bundler
in addition to the gem? [Yn] Y
```

**3.**

Install version of bundler that does the things right

```
gem install bundler -v=1.12.0
```

**4.**

Remove `Gemfile.lock`

```
rm -f Gemfile.lock
```

**5.**

Bundle it!

```
bundle

The path `/PATH/TO/RELEASES/test_case/Gemfiles/gems/gem1` does not exist.
```

**6.**

Let's try to change path to gems in `Gemfiles/specific_1.rb`

```
[edit tool] Gemfiles/specific_1.rb
```

```
# gem 'gem1', path: './gems/gem1'
# gem 'gem2', path: './gems/gem2'

gem 'gem1', path: '../gems/gem1'
gem 'gem2', path: '../gems/gem2'
```

**6.**

Try to bundle it now

```
$ bundle

Fetching gem metadata from https://rubygems.org/
Fetching version metadata from https://rubygems.org/
Resolving dependencies...
Using gem1 0.1.0 from source at `../gems/gem1`
Using gem2 0.1.0 from source at `../gems/gem2`
Using bundler 1.12.0
Bundle complete! 2 Gemfile dependencies, 3 gems now installed.
Use `bundle show [gemname]` to see where a bundled gem is installed.
```

And yet another time

```
$ bundle

The path `/PATH/TO/RELEASES/gems/gem1` does not exist.
```
