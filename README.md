import java.util.ArrayList;
import java.util.Scanner;

public class AutoboxingSum {

    public static void main(String[] args) {
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
                int primitiveInt = Integer.parseInt(input);
                numbers.add(primitiveInt); 
                System.out.println("Added: " + primitiveInt);

            } catch (NumberFormatException e) {
                System.out.println("Invalid input. Please enter a valid integer or 'done'.");
            }
        }

        long totalSum = 0;
        
        System.out.print("\nCalculating sum for: [");
        
        for (Integer numObj : numbers) {
            int number = numObj;
            totalSum += number;
            System.out.print(number + (numbers.indexOf(numObj) < numbers.size() - 1 ? ", " : ""));
        }
        
        System.out.println("]");
        System.out.println("\nTotal Sum using Unboxing: " + totalSum);

        scanner.close();
    }
}
