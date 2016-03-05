# ExConstructor

[![wercker status](https://app.wercker.com/status/f2dbf92012667da4ac8511f619da4429/s/master "wercker status")](https://app.wercker.com/project/bykey/f2dbf92012667da4ac8511f619da4429)
[![Coverage Status](https://coveralls.io/repos/github/appcues/exconstructor/badge.svg?branch=master)](https://coveralls.io/github/appcues/exconstructor?branch=master)
[![Hex.pm Version](http://img.shields.io/hexpm/v/exconstructor.svg?style=flat)](https://hex.pm/packages/exconstructor)

ExConstructor is an Elixir library that makes it easy to instantiate
structs from external data, such as that emitted by a JSON parser.

Add `use ExConstructor` after a `defstruct` statement to inject
a constructor function into the module.

The generated constructor, called `new` by default,
handles input format differences automatically,
DRYing up your code and letting you move on to the interesting
parts of your program.

* Input structure: Map or Keyword/2-tuple list
* Key type: String or Atom
* Key format: camelCase, under_score, dash-er-ized

## Example

```elixir
defmodule TestStruct do
  defstruct field_one: 1,
            field_two: 2,
            field_three: 3,
            field_four: 4,
            field_five: 5
  use ExConstructor
end

TestStruct.new(%{"field_one" => "a", "fieldTwo" => "b", :field_three => "c",
                 :fieldFour => "d", "field-five" => "e"})
# => %TestStruct{field_one: "a", field_two: "b", field_three: "c",
                 field_four: "d", field_five: "e"}
```

## [Full Documentation](http://hexdocs.pm/exconstructor/ExConstructor.html)

[Full ExConstructor documentation is available on
Hexdocs.pm.](http://hexdocs.pm/exconstructor/ExConstructor.html)


## Authorship and License

ExConstructor is copyright 2016 Appcues, Inc.

ExConstructor is released under the
[MIT License](https://github.com/appcues/exconstructor/blob/master/LICENSE.txt).

