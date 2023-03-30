# test
```
import org.junit.jupiter.api.Test;
import org.testcontainers.containers.GenericContainer;
import org.testcontainers.utility.DockerImageName;

public class DynamoDBLocalTest {

    @Test
    public void testDynamoDBLocal() {
        try (GenericContainer<?> container = new GenericContainer<>(DockerImageName.parse("amazon/dynamodb-local:latest"))
                .withExposedPorts(8000)
                .withCommand("-jar", "DynamoDBLocal.jar", "-inMemory", "-sharedDb")) {

            container.start();

            // You can now connect to DynamoDB Local on the container's IP address and exposed port
            String endpoint = "http://" + container.getHost() + ":" + container.getFirstMappedPort();
            System.out.println("DynamoDB Local endpoint: " + endpoint);

            // Do your tests here

        }
    }
}
```
