import java.util.ArrayList;
import java.util.Scanner;

/**
 * Part A: Demonstrates Autoboxing, Unboxing, and String Parsing.
 * The program accepts string inputs, converts them to Integer objects (autoboxing occurs here),
 * stores them in an ArrayList, and then sums them up (unboxing occurs during the sum calculation).
 */
public class AutoboxingSum {

    public static void main(String[] args) {
        // Use ArrayList<Integer> to store Integer objects
        ArrayList<Integer> numbers = new ArrayList<>();
        Scanner scanner = new Scanner(System.in);
        String input;
        
        System.out.println("--- Sum of Integers using Autoboxing/Unboxing ---");
        System.out.println("Enter integers one by one (type 'done' to calculate sum):");

        while (true) {
            System.out.print("Enter integer (or 'done'): ");
            input = scanner.nextLine().trim();

            if (input.equalsIgnoreCase("done")) {
                break;
            }

            try {
                // 1. String Parsing: Convert string input to primitive int
                int primitiveInt = Integer.parseInt(input);
                
                // 2. Autoboxing: The primitive int is automatically converted to an Integer object 
                //    when added to the ArrayList<Integer>.
                numbers.add(primitiveInt); 
                System.out.println("Added: " + primitiveInt + " (Autoboxing occurred)");

            } catch (NumberFormatException e) {
                System.out.println("Invalid input. Please enter a valid integer or 'done'.");
            }
        }

        // Calculate the sum of the numbers in the ArrayList
        long totalSum = 0;
        
        System.out.print("\nCalculating sum for: [");
        
        // 3. Unboxing: In the enhanced for-loop, the Integer object 'numObj' 
        //    is automatically converted back to a primitive 'int' when assigned to the 'number' variable.
        for (Integer numObj : numbers) {
            int number = numObj; // This is where Unboxing happens implicitly
            totalSum += number;
            System.out.print(number + (numbers.indexOf(numObj) < numbers.size() - 1 ? ", " : ""));
        }
        
        System.out.println("]");
        System.out.println("\nTotal Sum using Unboxing: " + totalSum);

        scanner.close();
    }
}
