# Cycromatic

Cycromatic calculates cyclomatic complexity of Ruby programs.

* Cyclomatic Complexity - https://en.wikipedia.org/wiki/Cyclomatic_complexity

## Installation

Install by `gem`:

    $ gem install cycromatic

## Usage

Ruby `cycromatic` command to calculate complexity:

```
$ cycromatic ruby_program.rb    # Specify paths to .rb files
$ cycromatic app config         # Specify directories including .rb files
```

The output of a file ([translator.rb](https://github.com/soutaro/contror/blob/e06797997f7b08ded4987f012704d2de04106afa/lib/contror/anf/translator.rb)) will look like the following:

```
$ cycromatic ../contror/lib/contror/anf/translator.rb
../contror/lib/contror/anf/translator.rb	[toplevel]:1:589	1
../contror/lib/contror/anf/translator.rb	initialize:8:11	1
../contror/lib/contror/anf/translator.rb	translate:14:18	1
../contror/lib/contror/anf/translator.rb	with_new_block:20:35	3
../contror/lib/contror/anf/translator.rb	current_block:37:39	1
../contror/lib/contror/anf/translator.rb	push_stmt:41:44	1
../contror/lib/contror/anf/translator.rb	normalize_node:46:57	3
../contror/lib/contror/anf/translator.rb	translate0:59:476	52
../contror/lib/contror/anf/translator.rb	translate_arg:478:489	3
../contror/lib/contror/anf/translator.rb	translate_call:491:531	2
../contror/lib/contror/anf/translator.rb	translate_params:533:545	2
../contror/lib/contror/anf/translator.rb	value_node?:547:564	7
../contror/lib/contror/anf/translator.rb	fresh_var:566:569	1
../contror/lib/contror/anf/translator.rb	translate_var:571:586	5
```

Each line consists of three columns:

* Path to file
* Method name or `[toplevel]` `:` first line `:` last line
* Complexity, or `[error]` if failed

You can give `--format=json` option to output calculated metric as JSON format.

```json
$ cycromatic --format json ../contror/lib/contror/anf/translator.rb | jq .
[
  {
    "path": "../contror/lib/contror/anf/ast/stmt.rb",
    "results": [
      {
        "method": "[toplevel]",
        "line": [
          1,
          522
        ],
        "complexity": 1
      },
      {
        "method": "initialize",
        "line": [
          9,
          12
        ],
        "complexity": 1
      },
      ....
    ]
  },
]
```

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/[USERNAME]/cycromatic.
