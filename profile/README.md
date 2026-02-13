# Obsidian Framework

> Modern web framework built on Spark Java with annotation-based routing, authentication, middleware, database migrations, and real-time capabilities.

**Features:** Annotation Routing • Auto-Discovery • Authentication • CSRF • Middleware • Flash Messages • ActiveJDBC • Migrations • Repositories • WebSockets • SSE • Dependency Injection

```java
@Controller
public class ArticleController extends BaseController
 {    
    @Before(AuthMiddleware.class)
    @GET(value = "/articles", name = "articles.index")
    private Object index(ArticleRepository repo) {
        return render("articles/index.html", Map.of(
            "articles", DB.withConnection(() -> repo.findAll())
        ));
    }
}
```

## Repositories

- **[core](https://github.com/obsidian-framework/core)** - The framework itself
- **[skeleton](https://github.com/obsidian-framework/skeleton)** - Boilerplate to start quickly
- **[realtime-examples](https://github.com/obsidian-framework/realtime-examples)** - WebSocket & SSE demos

## Quick Start

```xml
<dependency>
  <groupId>io.github.kainovaii</groupId>
  <artifactId>obsidian-core</artifactId>
  <version>1.0.3</version>
</dependency>
```

📚 Full docs at [obsidian.kainovaii.dev](https://obsidian.kainovaii.dev)

## Philosophy

Developer-friendly, not opinionated. Obsidian gives you useful abstractions without forcing rigid patterns. Use what you need, ignore the rest.

Built on the [community-maintained Spark fork](https://github.com/sparkjava-community) with support for Java 11, 17, and 21.
