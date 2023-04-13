# Integration tests

**Integration testing** is the second level of the software testing process comes after unit testing. In this testing,
units or individual components of the software are tested in a group. The focus of the integration testing level is to
expose defects at the time of interaction between integrated components or units.

## Co będziemy testować

Test polega na badaniu rezultatu współpracy wszystkich komponentów na przekroju przez aplikację. Np.
> endpoint → controller ←→ service ←→ repository ←→ database

[Architecture-flow-of-spring-boot](https://my.visme.co/view/8r49go6m-architecture-flow-of-spring-boot)

## Integration Test Example

```java
@RunWith(SpringRunner.class)
@SpringBootTest
@AutoConfigureMockMvc
public class UserControllerIntegrationTest {

    @Autowired
    private MockMvc mockMvc;

    @Autowired
    private ObjectMapper objectMapper;

    @Autowired
    private UserRepository userRepository;

    @Test
    public void whenPostRequestToUsersAndValidUser_thenCorrectResponse() throws Exception {
        UserDto user = new UserDto("John", "Doe");

        mockMvc.perform(post("/users")
                        .contentType(MediaType.APPLICATION_JSON)
                        .content(objectMapper.writeValueAsString(user)))
                .andExpect(status().isCreated())
                .andExpect(jsonPath("$.firstName", is(user.getFirstName())))
                .andExpect(jsonPath("$.lastName", is(user.getLastName())));

        User savedUser = userRepository.findAll().get(0);
        assertThat(savedUser.getFirstName()).isEqualTo(user.getFirstName());
        assertThat(savedUser.getLastName()).isEqualTo(user.getLastName());
    }
}
```

This integration test uses MockMvc to simulate an HTTP request and test the entire stack of the application, including
the controller, service, and repository layers. The test ensures that the UserController correctly handles the request
and that the data is saved in the database.

This test example follow good practices for testing in Spring Boot. Uses MockMvc to test the entire stack. The test is well-organized, 
use descriptive names, and ensure that the code is well-tested.

## Links

- [Integration Testing in Spring](https://www.baeldung.com/integration-testing-in-spring)


