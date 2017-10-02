# Apache Commons and Guava

# Apache Commons

##

- set of fore libraries for almost everything you can think of:
  - collections, IO, email, primitives, network utilities, logging, Excel and CSV parsing, CLI parsing, crypto, compression...
- divided in to 3 parts: proper (stable, under active development), sandbox (unstable, under active development), dormant (inactive)

##

```xml
<dependency>
  <groupId>org.apache.commons</groupId>
  <artifactId>commons-lang3</artifactId>
  <version>3.6</version>
</dependency>

<dependency>
    <groupId>org.apache.commons</groupId>
    <artifactId>commons-collections4</artifactId>
    <version>4.1</version>
</dependency>
```

# Guava

##

- set of core libraries for:
  - collections
  - graphs
  - caching
  - IO
  - functional types
  - hashing
  - primitives
  - ...
- policy for never removing APIs (except those marked with `@Beta`)
- Java9 compatible
- new release every 2 weeks
- thoroughly tested (more than 280000 tests!!!) and optimized

##

```xml
<dependency>
  <groupId>com.google.guava</groupId>
  <artifactId>guava</artifactId>
  <version>23.1-jre</version><!-- for Android: 23.1-android -->
</dependency>
```

# Apache commons

## Pair, Triple

- immutable and mutable versions
- don't overuse
```java
Pair.of(key, value)
Triple.of(first, second, third)
```

## StringUtils

- null safe
- various character checks (isNumeric, isWhitespace, isAsciiPrintable, isBlank, isEmpty,...)
- various content checks (starts with, ends with, contains, difference,...)
- various character manipulations (rotate, reverse, trim, split, join, pad right, pad left, to upper, to lower, capitalize,...)

```java
StringUtils.wrap("myString", '"'); // myString -> "myString"
StringUtils.unwrap("\"myString\"", '"'); // "myString" -> myString
StringUtils.abbreviate("abcdefg", 6); // abcdefg -> abc...
StringUtils.isAlpha("myString");  // true
```

```java
// before
if (s != null && !s.isEmpty()) {
    // ...
}
// after
if (isNotEmpty(s)) {
    // ...
}
```

## ArrayUtils

- null safe
- various checks (isEmpty, isSorted, lastIndexOf)
- various content manipulations:
  - shuffle, reverse, shift, swap
  - add, addAll, remove, removeAllOccurrences
 - clone, subarray, ...

## CollectionUtils

- null safe
- in Java8 most of the methods can be replaced with stream operations
- various checks (isEmpty, isNotEmpty, isSubCollection, isEqualCollection)
- permutations

# Apache commons - IteratorUtils

- null safe
- must methods can be replaced with Java8 streams
- loopingIterator, toArray, forEachButLast,...

# Guava - Preconditions

- contains a number of precodition checking utilities
- simple and unambiguous

```java
// before
if (!myArg.hasSomething) {
  throw new IllegalArgumentException("oh no it hasn't");
}

// after
checkArgument(!myArg.hasSomething, "oh no it hasn't");
```

# Guava Immutable collections
- TODO

# Guava - BiMap
- TODO

# Guava - Multimap, Multiset
- TODO

# Guava - Table
- TODO

# Guava - Range
- TODO

# Guava - Sets
- TODO

# Sets.difference
- TODO

# Sets.union
- TODO

# Sets.intersection)
- TODO

# Guava - other goodies
- Math and primitives
- EventBus
- Graphs
- Equals|HashCode builders
- Caching
- BloomFilters

