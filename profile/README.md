<p align="center">
  <a href="https://obsidian-java.com/" target="_blank">
    <img src="https://obsidian-java.com/assets/img/logo.png" width="300" alt="Obsidian Framework">
  </a>
  <br /><br />
</p>

Modern Java web framework built on Spark. Convention over configuration — annotation-based routing, dependency injection, database migrations, middleware, and real-time capabilities without the boilerplate.

Full docs at [https://obsidian-java.com/docs](https://obsidian-java.com/docs)

## Quick look

```java
@Controller
public class UserController extends BaseController
 {
    @Inject
    private UserRepository userRepository;

    @GET("/users")
    public String index(Request req, Response res) {
        return render("users/index.html", map("users", userRepository.findAll()));
    }

    @POST("/users")
    @CsrfProtect
    public String store(Request req, Response res) {
        userRepository.create(req.queryParams("name"), req.queryParams("email"));
        return redirectWithFlash("/users", "User created.");
    }
}
```

```java
public class CreateUsersTable extends Migration
{
    @Override
    public void up() {
        create("users", table -> {
            table.id();
            table.string("name").notNull();
            table.string("email").notNull().unique();
            table.timestamps();
        });
    }
}
```

## Philosophy
Clear structure, no ceremony. Obsidian gives you useful conventions without forcing rigid patterns — use what you need, ignore the rest.

Built on the [community-maintained Spark fork](https://github.com/sparkjava-community) with support for Java 11, 17, and 21.
