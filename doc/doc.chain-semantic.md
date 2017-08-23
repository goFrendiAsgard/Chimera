# YAML chain Semantic

Chimera is a Component Based Software Engineering Framework. In order to define the orchestration of the components, a YAML chain file is required.

All chain file should contains single `Root Process`. The semantic of YAML chain file is specified as follow:

## Root_process

Complete `Root_process` is as follow:

```yaml
vars: [Variable_declaration]
verbose: [Boolean]
[Process]
```

In some cases, you can ommit `Variable_declaration` and verbosity behavior.

```yaml
[Process]
```

## Boolean

Boolean has two possible value, `true` or `false`

```yaml
true
```

```yaml
false
```

## Variable_declaration

`Variable_declaration` consists of `Variable_name : Value` pairs

```yaml
[Variable_name] : [Value]
[Variable_name] : [Value]
...
```

## Variable_name

Any valid `String` can be used as `Variable_name`

```yaml
[String]
```

## Value

Any valid `String` can be used as `Value`

```yaml
[String]
```

## Process

There are several ways to write `Process`

```yaml
ins: [Input]
out: [Output]
mode: [Mode]
chains:
    - [Process]
    - [Process]
    - ...
```

```yaml
ins: [Input]
out: [Output]
[Mode]:
    - [Process]
    - [Process]
    - ...
```

```yaml
ins: [Input]
out: [Output]
command: [Command]
```

`Process` can also be written in a single line

```yaml
([Input]) -> [Command] -> [Output]
```

```yaml
([Input]) -> [Command]
```

```yaml
[Command] -> [Output]
```

## Mode

`Mode` is either `serial` or `parallel`

```yaml
series
```

```yaml
parallel
```

## Input

`Input` is comma separated `Value` or `Variable_name`.

```yaml
[Variable_name], [Variable_name], [Variable_name], ...
```

```yaml
"[Value]", "[Value]", "[Value]", ...
```

The combination of `Value` and `Variable_name` is also permitted.

```yaml
[Variable_name], "[Value]", ...
```

## Output

```yaml
[Variable_name]
```

## Command

Any non-interactive command prompt program can be used as `Cmd_command`.
E.g: `cal`, `calc`, `php your-script.php`, `python your-script.py`, `node your-script.js`, etc.

```yaml
Cmd_command
```

Javascript arrow function [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions) can be used as `Command`

```yaml
Javascript_arrow_function
```