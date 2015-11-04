# powur: simple js package manager

Powur is a simple package manager for javascript libraries that is not based
on a repository. This allows installing any package that exists on GitHub.
Currently only GitHub is supported as a source. The `version` specifies what
versions to match using the standard matching format with `~`, `^`, `>`, `>=`,
`<` or `<=`. The `url` specifies where to download the package which must be
either a `zip`, `tar` or `tar.gz` file. The `version_url` specifies where to
get a list of released versions of a package currently only GitHub tags or
releases can be used. Included files are mapped in `include` the key being the
file to match with double wildcard support and the value being the output
location. Output directory must have a tailing `/`. The keywords `{name}` and
`{version}` can be used to refrence the packages name and version. Below is an
example `powur.json` configuration, to download the packages run
`python2 powur.py install`.

```json
{
    "powur": {
        "vendor_path": "vendor",
        "temp_path": "vendor/powur_temp"
    },
    "traceur": {
        "version": "~0.0.92",
        "url": "https://github.com/google/traceur-compiler/archive/gh-pages.zip",
        "version_url": "github://github.com/google/traceur-compiler/tags",
        "include": {
            "traceur-compiler-gh-pages/bin/*": "{name}/"
        }
    },
    "systemjs": {
        "version": "~0.19.5",
        "url": "https://github.com/systemjs/systemjs/archive/{version}.zip",
        "version_url": "github://github.com/systemjs/systemjs/releases",
        "include": {
            "{name}-{version}/dist/*": "{name}/"
        }
    },
    "react": {
        "version": "~0.14.2",
        "url": "https://github.com/facebook/react/releases/download/v{version}/react-{version}.zip",
        "version_url": "github://github.com/facebook/react/releases",
        "include": {
            "{name}-{version}/build/*": "{name}/"
        }
    },
    "flux": {
        "version": "~2.1.1",
        "url": "https://github.com/facebook/flux/archive/{version}.zip",
        "version_url": "github://github.com/facebook/flux/tags",
        "include": {
            "{name}-{version}/dist/*": "{name}/"
        }
    },
    "jquery": {
        "version": "~2.1.4",
        "url": "https://github.com/jquery/jquery/archive/{version}.tar.gz",
        "version_url": "github://github.com/jquery/jquery/tags",
        "include": {
            "{name}-{version}/dist/*": "{name}/"
        }
    },
    "polymer": {
        "version": "~1.0.0",
        "url": "http://zipper.bowerarchiver.appspot.com/archive?polymer=Polymer/polymer#{version}",
        "version_url": "github://github.com/Polymer/polymer/releases",
        "include": {
            "components/bower_components/{name}/*.html": "{name}/"
        }
    },
    "paper-elements": {
        "version": "~1.0.0",
        "url": "http://zipper.bowerarchiver.appspot.com/archive?polymer=PolymerElements/paper-elements#{version}",
        "version_url": "github://github.com/PolymerElements/paper-elements/releases",
        "include": {
            "components/bower_components/**/*.html": "",
            "components/bower_components/**/*.css": "",
            "components/bower_components/**/*.js": "",
            "components/bower_components/**/*.map": "",
            "components/bower_components/**/*.gz": ""
        }
    }
}
```
