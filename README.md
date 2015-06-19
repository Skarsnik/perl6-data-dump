# Data::Dump 

## for perl6

that's right folks, here's a quicky for your data dump needs.  if you have Term::ANSIColor installed then the output will be so colorful your eyes might bleed.

feel free to submit bugs or make suggestions, if you submit a bug please provide a concise example that replicates the problem and i'll add some tests and make this thing better.

## usage

```perl6
use Data::Dump;

say Dump(%( 
  key1 => 'value1',
  key256 => 1,
));
```

output:
```
{
  key1   => "value1".Str,
  key256 => 1.Int,
}
```
note: if you have Term::ANSIColor installed then it's going to be amazing. so, prepare yourself.

## oh you want to your custom class?

here you go, dude

```perl6
use Data::Dump;

class E {
  has $.public;
  has Int $!private = 5;
  method r(Str $a) { };
  method s($b, :$named? = 5) { };
  method e returns Int { say $!private; };
};

say Dump(E.new);
```

output:
```
E :: (
  $!private => 5.Int,
  $!public  => (Any),

  method e () returns Int {...},
  method public () returns Mu {...},
  method r (Str $a) returns Mu {...},
  method s (Any $b, Any :named($named) = 5) returns Mu {...},
)
```
