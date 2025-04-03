import javafx.application.Application;
import javafx.scene.Scene;
import javafx.scene.control.Button;
import javafx.scene.control.Label;
import javafx.scene.control.PasswordField;
import javafx.scene.control.TextField;
import javafx.scene.layout.GridPane;
import javafx.stage.Stage;

public class LMSFrontend extends Application {
    @Override
    public void start(Stage primaryStage) {
        primaryStage.setTitle("LMS - Login");

        // Login UI Components
        Label userLabel = new Label("Username:");
        TextField userTextField = new TextField();
        Label passLabel = new Label("Password:");
        PasswordField passTextField = new PasswordField();
        Button loginButton = new Button("Login");
        Label messageLabel = new Label();
        
        // Layout
        GridPane grid = new GridPane();
        grid.setHgap(10);
        grid.setVgap(10);
        grid.add(userLabel, 0, 0);
        grid.add(userTextField, 1, 0);
        grid.add(passLabel, 0, 1);
        grid.add(passTextField, 1, 1);
        grid.add(loginButton, 1, 2);
        grid.add(messageLabel, 1, 3);
        
        // Login Button Action
        loginButton.setOnAction(e -> {
            String username = userTextField.getText();
            String password = passTextField.getText();
            if (username.equals("admin") && password.equals("admin")) {
                messageLabel.setText("Login successful!");
                openDashboard(primaryStage);
            } else {
                messageLabel.setText("Invalid credentials");
            }
        });
        
        Scene loginScene = new Scene(grid, 300, 200);
        primaryStage.setScene(loginScene);
        primaryStage.show();
    }
    
    private void openDashboard(Stage primaryStage) {
        Label welcomeLabel = new Label("Welcome to the LMS Dashboard!");
        Button logoutButton = new Button("Logout");
        
        logoutButton.setOnAction(e -> start(primaryStage));
        
        GridPane dashboardGrid = new GridPane();
        dashboardGrid.setVgap(10);
        dashboardGrid.add(welcomeLabel, 0, 0);
        dashboardGrid.add(logoutButton, 0, 1);
        
        Scene dashboardScene = new Scene(dashboardGrid, 400, 300);
        primaryStage.setScene(dashboardScene);
    }
    
    public static void main(String[] args) {
        launch(args);
    }
}
