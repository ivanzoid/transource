Utility to automatically convert C++-style comments in source code from any language to English.

### Limitations

It's pretty dumb at the moment, it will not translate multiline (`/* */`) comments, and it will not try to translate consecutive comments as a single whole.

### Prerequisites

1. `sudo pip install microsofttranslator`

2. Get your `Client ID` and `Client Secret` from Microsoft, read instructions at [microsofttranslator's lib page](https://github.com/openlabs/Microsoft-Translator-Python-API)

### (Optional) Configure

Create `~/.transource.cfg` with contents like this (it's in JSON formt):

```
{
	"clientId": "your client id",
	"clientSecret": "your client secret"
}
```

### Running

If you've configured your `~/.transource.cfg` at previous step, then just run:

`transource <sourcefile> > <outputFile>`

Or if not, pass your secret values as command-line options:

`transource --cid <yourClientId> --secret <yourClientSecret> <sourcefile> > <outputFile>`


### Mass-processing

For mass-translating of lots of files I use this (make sure you have backups of your files before running, of course):

`find . -name '*.[hc]' -exec sh -c 'transource {} > {}.tmp && mv {}.tmp {}' \;`

