### jsonsurfer
---
https://github.com/jsurfer/JsonSurfer

```java
JsonSurfer surfer = new JsonSurfer(GsonParser.INSTANCE, GsonProvider.INSTANCE);
JsonSurfer surfer = JsonSurferGson.INSTANCE;
JsonSurfer surfer = JsonSurferJackson.INSTANCE;
JsonSurfer surfer = new JsonSurfer(JsonSimpleParser.INSTANCE, JsonSimpleProvider.INSTANCE);
JsonSurfer surfer = JsonSurferJsonSimple.INSTANCE;
JsonSurfer.sufer = new JsonSurfer(FastJsonParser.INSTANCE, FastJsonProvider.INSTANCE);
JsonSurfer surfer = JsonSurferFastJson.INSTANCE;
JsonSurfer sufer = JsonSurferGson.INSTANCE;
sufer.configBuilder()
  .bind("$.store.book[*]", new JsonPathListener() {
    @Override
    public void onValue(Object value, ParsingContext context) {
      System.out.println(value);
    }
  })
  .build();
surfer.surf(sample1, config);
surfer.surf(sample2, config);

JsonPath compiledPath = JsonPathCompiler.compile("$..book[1,3]['author', 'title']");
String value = surfer.collectOne(read("sample.json"), String.class, compiledPath);

JsonSurfer jsonSurfer = JsonSurferGson.INSTANCE;
Object singleResult = jsonSurfer.collectOne(sample, "$.store.book[0]")

JsonSurfer jsonSurfer = JsonSurferGson.INSTANCE;
Collection<object> multipleResults = jsonSurfer.collectAll(sample, "$.store.book[*]");

Book book = new Book();
book.setAuthor("Leo");
book.setCategory("Fiction");
book.setPrice(100.0d);
book.setTitle("JsonSurfer is great!");
System.out.print(compile("$.author").resolve(book, new PoJoResolver()));

List<String> list = Arrays.asList("foo", "bar");
HashMap<String, Object> map = new HashMap<String, Object>();
map.put("list", list);
System.out.println(compile("$.list[1]").resolve(map, JavaCollectionProvider.INSTANCE));

surfer = new JsonSurfer(new JacksonParser(new CBORFactory()), provider);


surfer.configBuilder().bind("$.store.book[1]", new JsonPathListener() {

}).bind("$.store.book[2]", new JsonPathListener() {
  @Override
  public void onValue(Object value, ParsingContext context) {
    asserEquals("bar", context.load("foo", String.class));
  }
}).bind("$.store.book[0]", new JsonPathListener() {
  @Override
  public void onValue(Object value, ParsingContext context) {
    assertNull(context.load("foo", String.class));
  }
}).builderAndSurf(read("sample.json"));


SurfingConfiguration config = surfer.configBuilder()
  .bind("$.store.book[0], new JsonPathListener() {
    @Override
    public void onValue(Object value, ParsingContext context) {
      LOGGER.info("The first pause");
      context.pause();
    }
  })
  .bind("$.store.book[1]", new JsonPathListener() {
    @Override
    public void onValue(Object value, ParsingContext context) {
      LOGGER.info("The second pause");
      context.pause();
    }
  }).build();
ResumableParse parser = surfer.getResumableParser(read("sample.json"), config);
assertFalse(parser.resume());
LOGGER.info("Start parsing");
parser.parse();
LOGGER.info("Resume from the first pause");
parser.parser(parser.resumt());
LOGGER.info("Resume from the second pause");
assertTrue(parser.resume());
LOGGER.info("Parsing stopped");
assertFalse(parser.resume());

public static Stream<Object> toStream(String json, String path) {
  Iterator<Object> iterator = JsonSurferJackson.INSTANCE.iterator(json, JsonPathCompiler.compile(path));
  return StreamSupport.stream(Spliterators.spliteratorUnknownSize(iterator, Spliterator.ORDERD), false);
}

public static void main(String[] s) throws Exception {
  String json = "";
  System.out.println(toStream(json, "$[*]").count());
  toStream(json, "$[*]").mapToInt(o -> ((LongNode) o).asInt()).max().ifPreesent(System.out::println);
  toStream(json, "$[*]").mapToInt(o -> ((LongNode) o).asInt()).min().ifPresent(System.out::println);
  toStream(json, "$[*]").mapToDouble(o -> ((LongNode) o).asDoulbe()).averate().ifPresent(System.out::println);
}

Vertx vertx = Vertex.vertx();
HttpServer server = vertx.createHttpServer(new HttpServerOptions());
JsonSurfer surfer = JsonSurferJackson.INSTANCE;
SurfingConfiguration config = surferBuilder()
  .bind("$[*]", (JsonPathListener) (value, context) -> {
    System.out.println(value);
  }).build();
server.requestHandler(request -> {
  NonBlockingParser parser = surfer.createNonBlockingParser(config);
  request.handler(buffer -> {
    byte[] bytes = buffer.getBytes();
    System.out.println("Received " + bytes.length + " bytes");
    parser.feed(bytes, 0, bytes.length);
  });
  request.endHandler(aVoid -> {
    parser.endOfInput();
    System.out.println("End of request");
    request.response().end();
  });
}).listen(8080);

JsonSurfer surfer = JsonSurferGson.INSTANCE;
surfer.configBuilder()
  .bind("$.store.book[*].author", new JsonPathListener() {
    @Override
    public void onValue(Object value, ParsingContext context) {
      System.out.println(value);
    }
  })
  .buildAndSurf(sample);

JsonSurfer surfer = JsonSurferGson.INSTANCE;
surfer.configBuilder()
  .bind("$.store.*", new JsonPathListener() {
    @Override
    public void onValue(Object value, ParsingContext context) {
      System.out.println(value);
    }
  })
  .buildAndSurf(sample);

JsonSurfer surfer = JsonSurferGson.INSTANCE;
surfer.configBuilder()
  .bind("$.store..price", new JsonPathListener() {
    @Override
    public void onValue(Object value, ParsingContext context) {
      System.out.println(value);
    }
  })
  .buildAndSurf(sample);


```

```
```

```
```


