import java.util.HashMap;
import java.util.Map;
import java.util.Scanner;
import java.util.regex.Matcher;
import java.util.regex.Pattern;

public class DogeAI {

    private static String userName = "Anonymous";
    private static String userLanguage = "English";
    private static Map<String, Map<String, String>> languageGreetings = new HashMap<>();
    private static Map<String, Map<String, String>> languageResponses = new HashMap<>();
    private static final String RICKROLL_REGEX = "https?://(?:www\\.)?youtu(?:\\.be/|be\\.com/(?:watch\\?v=|v/|embed/|.*[?&]v=))([^&#?\\n]+)";

    public static void main(String[] args) {
        // Initialize language-specific greetings and responses for supported languages
        initializeLanguages();

        // Initialize scanner for user input
        Scanner scanner = new Scanner(System.in);

        // Prompt the user to enter their name
        System.out.print("Enter your name (or press Enter to continue anonymously): ");
        String inputName = scanner.nextLine();
        if (!inputName.isEmpty()) {
            userName = inputName;
        }

        // Prompt the user to select their language
        System.out.println("Select your language:");
        printLanguageOptions();
        int languageChoice = scanner.nextInt();
        if (languageChoice >= 1 && languageChoice <= 5) {
            userLanguage = getLanguageCode(languageChoice);
        }
        scanner.nextLine(); // Consume newline character left from nextInt()

        // Print debug prompt
        System.out.println(getDebugPrompt());

        // Start conversation loop
        system.out.println(getGreetingMessage(userLanguage) + " " + userName + "!");
        system.out.println(getResponseMessage(userLanguage));
        while (true) {
            // Get user input
            System.out.print(userName + ": ");
            String userInput = scanner.nextLine();

            // Debugging commands
            if (userInput.equals("!debug")) {
                // Print debug information
                printDebugInfo();
                continue;
            }

            // Check for rickroll
            if (isRickroll(userInput)) {
                System.out.println("RICKROLL DETECTED");
                continue;
            }

            // Check domain origin
            String domain = getDomainOrigin(userInput);
            if (domain != null) {
                System.out.println("Origin domain: " + domain);
                continue;
            }

            // Process user input
            String response = processInput(userInput, userLanguage);

            // Output AI response
            System.out.println("AI: " + response);
        }
    }

    // Initialize language-specific greetings and responses for supported languages
    private static void initializeLanguages() {
        // English greetings and responses
        Map<String, String> englishGreetings = new HashMap<>();
        englishGreetings.put("greeting", "Hello");
        languageGreetings.put("English", englishGreetings);

        Map<String, String> englishResponses = new HashMap<>();
        englishResponses.put("question", "How can I assist you?");
        languageResponses.put("English", englishResponses);

        // French greetings and responses
        Map<String, String> frenchGreetings = new HashMap<>();
        frenchGreetings.put("greeting", "Bonjour");
        languageGreetings.put("French", frenchGreetings);

        Map<String, String> frenchResponses = new HashMap<>();
        frenchResponses.put("question", "Comment puis-je vous aider?");
        languageResponses.put("French", frenchResponses);

        // Italian greetings and responses
        Map<String, String> italianGreetings = new HashMap<>();
        italianGreetings.put("greeting", "Ciao");
        languageGreetings.put("Italian", italianGreetings);

        Map<String, String> italianResponses = new HashMap<>();
        italianResponses.put("question", "Come posso aiutarti?");
        languageResponses.put("Italian", italianResponses);

        // Dutch greetings and responses
        Map<String, String> dutchGreetings = new HashMap<>();
        dutchGreetings.put("greeting", "Hallo");
        languageGreetings.put("Dutch", dutchGreetings);

        Map<String, String> dutchResponses = new HashMap<>();
        dutchResponses.put("question", "Hoe kan ik je helpen?");
        languageResponses.put("Dutch", dutchResponses);

        // Spanish greetings and responses
        Map<String, String> spanishGreetings = new HashMap<>();
        spanishGreetings.put("greeting", "Hola");
        languageGreetings.put("Spanish", spanishGreetings);

        Map<String, String> spanishResponses = new HashMap<>();
        spanishResponses.put("question", "¿Cómo puedo ayudarte?");
        languageResponses.put("Spanish", spanishResponses);
    }

    // Print language options for user selection
    private static void printLanguageOptions() {
        System.out.println("1. English");
        System.out.println("2. French");
        System.out.println("3. Italian");
        System.out.println("4. Dutch");
        System.out.println("5. Spanish");
    }

    // Get language code based on user selection
    private static String getLanguageCode(int languageChoice) {
        switch (languageChoice) {
            case 1:
                return "English";
            case 2:
                return "French";
            case 3:
                return "Italian";
            case 4:
                return "Dutch";
            case 5:
                return "Spanish";
            default:
                return "English"; // Default to English if invalid choice
        }
    }

    // Get greeting message based on user language
    private static String getGreetingMessage(String language) {
        Map<String, String> greetings = languageGreetings.get(language);
        return greetings.get("greeting");
    }

    // Get response message based on user language
    private static String getResponseMessage(String language) {
        Map<String, String> responses = languageResponses.get(language);
        return responses.get("question");
    }

    // Process user input based on language
    private static String processInput(String userInput, String language) {
        // Placeholder response
        return "Response to user input";
    }

    // Check if the input contains a rickroll link
    private static boolean isRickroll(String userInput) {
        Pattern pattern = Pattern.compile(RICKROLL_REGEX);
        Matcher matcher = pattern.matcher(userInput);
        return matcher.find();
    }

    // Get the origin domain of a URL
    private static String getDomainOrigin(String userInput) {
        // Placeholder implementation
        return null;
    }

    // Generate debug prompt message
    private static String getDebugPrompt() {
        String language = userLanguage;
        return String.format("DEBUG - Username: %s, Language: %s", userName, language);
    }

    // Debugging method to print debug information
    private static void printDebugInfo() {
        System.out.println("Debug Information:");
        System.out.println("User Name: " + userName);
        System.out.println("User Language: " + userLanguage);
        // Add more debug information as needed
    }
}
