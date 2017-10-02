# Apache Commons and Guava

# Introduction

## Apache Commons

- set of fore libraries for almost everything you can think of:
  - collections, IO, email, primitives, network utilities, logging, Excel and CSV parsing, CLI parsing, crypto, compression...
- divided in to 3 parts: proper (stable, under active development), sandbox (unstable, under active development), dormant (inactive)

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

## Guava

- set of core libraries for:
  - collections
  - graps
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

```xml
<dependency>
  <groupId>com.google.guava</groupId>
  <artifactId>guava</artifactId>
  <version>23.1-jre</version><!-- for Android: 23.1-android -->
</dependency>
```

-- APACHE COMMONS
- Pair
- Triple
- StringUtils
- ArrayUtils
- RandomUtils
- StringUtils
- CollectionUtils
- Bag

-- GUAVA
- BiMap, Multimap|Multiset, Immutable collections, Table, Range Collection methods(Sets.difference, Sets.union, Sets.intersection),

# Guava

##Preconditions

## Other goodies
- Math and primitives
- EventBus
- Graphs
- Equals|HashCode builders
- Caching
- BloomFilters