# Apache Commons and Guava

# Apache Commons

##

- set of fore libraries for almost everything you can think of:
    - collections, IO, email, primitives, network utilities, logging, Excel and CSV parsing, CLI parsing, crypto, compression...
- mandatory: lang (3), collections, text
- divided in to 3 parts:
    - proper (stable, under active development)
    - sandbox (unstable, under active development)
    - dormant (inactive)

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

- set of core libraries for: collections, graphs, caching, IO, functional types, hashing, ...
- policy for never removing APIs (except those marked with `@Beta`)
- Java9 compatible
- new release every 2 weeks
- thoroughly tested (more than 280000 tests!!!) and optimized

##

```xml
<dependency>
  <groupId>com.google.guava</groupId>
  <artifactId>guava</artifactId>
  <!-- for Android: 23.1-android -->
  <version>23.1-jre</version>
</dependency>
```

# Apache commons

##
### Pair, Triple

- in JDK: `AbstractMap.SimpleEntry`, `AbstractMap.SimpleImmutableEntry`
- immutable and mutable versions
- don't overuse

```java
Pair.of(key, value);
Triple.of(first, second, third);
```

##
### StringUtils

- null safe
- various character checks (`isNumeric`, `isWhitespace`, `isAsciiPrintable`, `isBlank`, `isEmpty`,...)
- various content checks (starts with, ends with, contains, difference,...)
- various character manipulations (rotate, reverse, trim, split, join, pad right, pad left, to upper, to lower, capitalize,...)

##
### StringUtils - examples

```java
// myString -> "myString"
StringUtils.wrap("myString", '"');

// "myString" -> myString
StringUtils.unwrap("\"myString\"", '"');

// abcdefg -> abc...
StringUtils.abbreviate("abcdefg", 6);

// true
StringUtils.isAlpha("myString");
```

##
### StringUtils - examples(2)

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

##
### ArrayUtils

- null safe
- various checks (isEmpty, isSorted, lastIndexOf)
- various content manipulations:
    - shuffle, reverse, shift, swap
    - add, addAll, remove, removeAllOccurrences
    - clone, subarray, ...

##
### ArrayUtils - examples

```java
TODO
```

##
### CollectionUtils

- null safe
- in Java8 most of the methods can be replaced with stream operations
- various checks (`isEmpty`, `isNotEmpty`, `isSubCollection`, `isEqualCollection`)
- permutations


##
### CollectionUtils - examples

```java
TODO
```

##
### IteratorUtils

- null safe
- most methods can be replaced with Java8 streams
- `loopingIterator`, `toArray`, `forEachButLast`,...

# Guava

##
### Preconditions

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

##
### Immutable collections

- thread safe
- simple to build and to use
- collection, set, list, map, multiset, multimap,...
- `Collections.unmodifiableX` - unsafe and inefficient wrappers around common collections


##
### Immutable collections - examples

```java
Set<String> s1 = ImmutableSet.of("a", "b");
Set<String> s2 = ImmutableSet.<String>builder()
  .add("a")
  .add("b")
  .build();
```

##
### Multiset

- useful when you have to count the number of occurences of an object
- similar to `Map<E, Long>`
- better version of Apache commons' `Bag`

##
### Multiset - examples

```java
TODO
```

##
### Multimap

- each key can contain a list or set of values
- similar to `Map<K, List<V>>` or `Map<K, Set<V>>` but with additional goodies

##
### Multimap - examples
```java
TODO
```

##
### BiMap

- TLDR: keys point to values, values point to keys
- easy way to maintain two separate maps and keep them in sync
- both keys and values have to be unique

##
### BiMap - examples

```java
TODO
```

##
### Range
- TODO

##
### Utility: Lists
- TODO

##
### Utility: Lists - examples
```java
TODO
```

##
### Utility: Sets
- TODO

##
### Utility: Sets - examples
```java
TODO
Sets.difference
Sets.union
Sets.intersection
```

##
### Utility: Maps
- TODO

##
### Utility: Maps - examples
```java
TODO
```


##
### Other goodies

- Math and primitives
- EventBus
- Graphs
- Equals|HashCode builders
- Caching
- BloomFilters

# Useful links

##

- Use Stream API simpler:
<https://medium.com/@tagir_valeev/use-stream-api-simpler-or-dont-use-it-at-all-ea0a44a4b1ff>

- Guava Wiki:
<https://github.com/google/guava/wiki>

- Apache commons official page:
<http://commons.apache.org/>

# Awaitility

TODO