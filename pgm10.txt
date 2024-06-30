import java.util.Scanner;
import java.security.MessageDigest;
import java.security.NoSuchAlgorithmException;

public class MDS {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        // Prompt user to enter the text
        System.out.print("Enter the text for which you want to calculate the message digest: ");
        String text = scanner.nextLine();
        
        try {
            // Create MessageDigest instance for MD5
            MessageDigest md = MessageDigest.getInstance("MD5");
            
            // Update input text in message digest
            md.update(text.getBytes());
            
            // Generate MD5 hash
            byte[] digest = md.digest();
            
            // Convert byte array to hexadecimal format
            StringBuilder hexString = new StringBuilder();
            for (byte b : digest) {
                hexString.append(String.format("%02x", b));
            }
            
            System.out.println("MD5 Hash: " + hexString.toString());
        } catch (NoSuchAlgorithmException e) {
            System.err.println("MD5 algorithm not found");
            e.printStackTrace();
        } finally {
            scanner.close();
        }
    }
}