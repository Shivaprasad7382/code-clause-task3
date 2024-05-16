import java.util.HashMap;

class User {
    private String username;
    private String facialFeatures;

    public User(String username, String facialFeatures) {
        this.username = username;
        this.facialFeatures = facialFeatures;
    }

    public String getUsername() {
        return username;
    }

    public String getFacialFeatures() {
        return facialFeatures;
    }
}

class FaceAuthenticationSystem {
    private HashMap<String, String> userFacialFeatures;

    public FaceAuthenticationSystem() {
        userFacialFeatures = new HashMap<>();
    }

    public void registerUser(User user) {
        userFacialFeatures.put(user.getUsername(), user.getFacialFeatures());
    }

    public boolean authenticateUser(User user) {
        String storedFacialFeatures = userFacialFeatures.get(user.getUsername());
        return storedFacialFeatures != null && storedFacialFeatures.equals(user.getFacialFeatures());
    }
}

public class Main {
    public static void main(String[] args) {
        FaceAuthenticationSystem authenticationSystem = new FaceAuthenticationSystem();

        User user1 = new User("Alice", "FacialFeatures1");
        User user2 = new User("Bob", "FacialFeatures2");

        authenticationSystem.registerUser(user1);
        authenticationSystem.registerUser(user2);

        // Simulating authentication process
        User userToAuthenticate = new User("Alice", "FacialFeatures1");
        boolean isAuthenticated = authenticationSystem.authenticateUser(userToAuthenticate);

        if (isAuthenticated) {
            System.out.println("User authenticated successfully!");
        } else {
            System.out.println("Authentication failed. Please try again.");
        }
    }
}
