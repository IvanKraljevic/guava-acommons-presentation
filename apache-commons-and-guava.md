# Apache Commons and Guava

# Apache Commons

##

- set of fore libraries for almost everything you can think of:
    - collections, IO, email, primitives, network utilities, logging, Excel and CSV parsing, CLI parsing, crypto, compression...
- divided in to 3 parts:
    - proper (stable, under active development)
    - sandbox (unstable, under active development)
    - dormant (inactive)
- mandatory: lang (3), collections, text

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

- various character checks (`isNumeric`, `isWhitespace`, `isAsciiPrintable`, `isBlank`, `isEmpty`,...)
- various content checks (starts with, ends with, contains, difference,...)
- various character manipulations (rotate, reverse, trim, split, join, pad right, pad left, to upper, to lower, capitalize,...)
- null safe

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
if (s != null && !s.isEmpty()) {...}

// after
if (isNotEmpty(s)) {...}
```

##
### ArrayUtils

- various checks (isEmpty, isSorted, lastIndexOf)
- various content manipulations:
    - shuffle, reverse, shift, swap
    - add, addAll, remove, removeAllOccurrences
    - clone, subarray, ...
- null safe

##
### ArrayUtils - examples

```java
int[] foo = ...

// before
if (foo != null && foo.length > 0) {...}

// after
if (ArrayUtils.isNotEmpty(foo)) {...}

ArrayUtils.contains(foo, 1));//...
```

##
### CollectionUtils

- in Java8 most of the methods can be replaced with stream operations
- various checks (`isEmpty`, `isNotEmpty`, `isSubCollection`, `isEqualCollection`)
- permutations
- null safe


##
### CollectionUtils - examples

```java
List<String> list = ...

// before
if (list != null && list.size() > 0) {...}

// after
if (CollectionUtils.isNotEmpty(list)) {...}
```

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

- collection, set, list, map, multiset, multimap,...
- simple to build and to use
- thread safe
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

- useful when you have to count the number of occurrences of an object
- similar to `Map<E, Long>`
- better version of Apache commons' `Bag`

##
### Multiset - examples

```java
Multiset<String> set = HashMultiset.create();
set.add("a");
set.add("b");
set.add("c", 5);
int five = set.count("c");
set.setCount("b", 0);
Set<String> elements = set.elementSet();
```

##
### Multimap

- each key can contain a list or set of values
- similar to `Map<K, List<V>>` or `Map<K, Set<V>>` but with additional goodies

##
### Multimap - examples
```java
Multimap<String, String> firstName2Nickname = HashMultimap.create();
firstName2Nickname.put("John", "Doe");
firstName2Nickname.put("John", "Brko");

// ["Doe", "Brko"]
Set<String> johns = firstName2Nickname.get("John");
```

##
### BiMap

- TLDR: keys point to values, values point to keys
- easy way to maintain two separate maps and keep them in sync
- both keys and values have to be unique

##
### BiMap - examples

```java
BiMap<String, Long> name2Id = HashBiMap.create();
String nameForId = name2Id.inverse().get(12L);
```

##
### Utility: Lists

- static constructors and factories
- various iterators, filters, mappers, etc. (similar operations to those offered by Java8 Stream API)


##
### Utility: Lists - examples
```java
List<String> l = Lists.newArrayList("a", "b", "c");
List<List<String>> partition = Lists.partition(l, 2);
```

##
### Utility: Sets

- static constructors and factories
- various iterators, filters, mappers, etc. (similar operations to those offered by Java8 Stream API)
- set-theoretic operations: union, intersection, difference, symmetric difference

##
### Utility: Sets - examples
```java
Set<String> s1 = Sets.newHashSet("a", "b", "c");
Set<String> s2 = Sets.newHashSet("c", "d", "e");

Sets.union(s1, s2); // [a, b, c, d, e]
Sets.intersection(s1, s2); // [c]
Sets.difference(s1, s2); // [a, b]
Sets.difference(s2, s1); // [d, e]
Sets.symmetricDifference(s1, s2); // [a, b, d, e]
```

##
### Utility: Maps

- static constructors and factories
- various iterators, filters, mappers, etc. (similar operations to those offered by Java8 Stream API)
- additional methods for inspecting differences between two lists

##
### Utility: Maps - examples
```java
Map<String, String> name2nickname = Maps.newHashMap(
  ImmutableMap.of("John", "Doe", "Jane", "Doe"));
Map<String, String> otherName2nickname = Maps.newLinkedHashMap(
  ImmutableBiMap.of("Foo", "Boo", "Hello", "World"));

Maps.difference(name2nickname, otherName2nickname).entriesInCommon();
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

- Guava Wiki:
<https://github.com/google/guava/wiki>

- Apache commons official page:
<http://commons.apache.org/>

- Use Stream API simpler:
<https://medium.com/@tagir_valeev/use-stream-api-simpler-or-dont-use-it-at-all-ea0a44a4b1ff>

# Awaitility

##

> Awaitility is a small Java DSL for synchronizing asynchronous operations

- See: <https://github.com/awaitility/awaitility>

```java
@Test
public void test() {
  // do something async
  await()
    .atMost(2, SECONDS)
    .until(userRepository::isEmpty);
}
```
