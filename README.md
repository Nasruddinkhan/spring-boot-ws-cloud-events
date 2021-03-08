# spring-boot-ws-cloud-events
spring boot example with cloud event

# test with code as well as use post man to test
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"username\": \"nasruddin\", \"firstName\": \"nasruddin\", \"lastName\": \"khan\", \"age\": 23}");
Request request = new Request.Builder()
  .url("http://localhost:8083/notification")
  .post(body)
  .addHeader("content-type", "application/json")
  .addHeader("ce-id", "1")
  .addHeader("ce-source", "cloud-event-example")
  .addHeader("ce-type", "notification.application")
  .addHeader("ce-specversion", "1.0")
  .build();

Response response = client.newCall(request).execute();
