import java.util.Scanner;

public class MainClass {

   public static void main(String[] args) {
     Scanner scanner = new Scanner(System.in);
     try {
        // Input: Gather student&#39;s information
        System.out.print(&quot;Enter Student Name: &quot;);
        String studentName = scanner.nextLine();
        
        System.out.print(&quot;Enter Course: &quot;);
        String course = scanner.nextLine();
        
        System.out.print(&quot;Enter Course Code: &quot;);
        String courseCode = scanner.nextLine();
        
        // Input for number of units with validation
        int numberOfUnits = 0;
        while (true) {
          System.out.print(&quot;Enter Number of Units (1-10): &quot;);
          if (scanner.hasNextInt()) {
              numberOfUnits = scanner.nextInt();
              if (numberOfUnits &gt;= 1 &amp;&amp; numberOfUnits &lt;= 10) {
                  break;
              } else {
                  System.out.println(&quot;Error: The number of units must
be between 1 and 10. Please try again.&quot;);
}
        } else {
            System.out.println(&quot;Error: Invalid input. Please enter a
number between 1 and 10.&quot;);
            scanner.next(); // Clear invalid input
        }
     }
  
     // Create an instance of the StudentEnrollment class
     StudentEnrollment student = new StudentEnrollment(studentName,
course, courseCode, numberOfUnits);

    // Compute the total enrollment fee
   int totalFee = student.calculateEnrollmentFee();
   
   // Output: Display the student&#39;s name and total fee
   System.out.println(&quot;\n--- Enrollment Summary ---&quot;);
   System.out.println(&quot;Student Name: &quot; + student.getStudentName());
   System.out.println(&quot;Course: &quot; + student.getCourse());
   System.out.println(&quot;Course Code: &quot; + student.getCourseCode());
   System.out.println(&quot;Number of Units: &quot; +
 student.getNumberOfUnits());
   System.out.println(&quot;Total Enrollment Fee: &quot; + totalFee);
   
   // Payment: Ask for the payment amount
   int payment = 0;
   while (true) {
       System.out.print(&quot;\nEnter payment amount: &quot;);
       if (scanner.hasNextInt()) {
           payment = scanner.nextInt();
           if (payment &gt;= 0) {
               break;
           } else {
               System.out.println(&quot;Error: Payment cannot be
negative. Please enter a valid amount.&quot;);
                    }
                  } else {
                      System.out.println(&quot;Error: Invalid input. Please enter a
valid amount.&quot;);
                      scanner.next(); // Clear invalid input
                  }
                 }
                 
                 // Check payment status
                 if (payment == totalFee) {
                     System.out.println(&quot;Payment Status: Fully Paid&quot;);
                 } else if (payment &lt; totalFee) {
                     System.out.println(&quot;Payment Status: Partial Payment&quot;);
                     System.out.println(&quot;Amount Paid: &quot; + payment);
                     System.out.println(&quot;Remaining Balance: &quot; + (totalFee -
payment));
                 } else {
                     System.out.println(&quot;Payment exceeds the total fee. Please
check the amount.&quot;);
            }
        } finally {
            scanner.close(); // Ensure the scanner is always closed
        }
    }
}
// Class StudentEnrollment
class StudentEnrollment {
    private String studentName;
    private String course;

   private String courseCode;
   private int numberOfUnits;
   private final int FEE_PER_UNIT = 1000; // Fixed fee per unit
   
   // Constructor to initialize student data
   public StudentEnrollment(String studentName, String course, String
courseCode, int numberOfUnits) {
        this.studentName = studentName;
        this.course = course;
        this.courseCode = courseCode;
        this.numberOfUnits = numberOfUnits;
    }
  // Method to calculate the total enrollment fee
  public int calculateEnrollmentFee() {
      return numberOfUnits * FEE_PER_UNIT;
    }
  // Getters for student&#39;s information
  public String getStudentName() {
  return studentName;
    }
    
  public String getCourse() {
  return course;
    }
    
  public String getCourseCode() {
  return courseCode;
    }

  public int getNumberOfUnits() {
  return numberOfUnits;
    } 
}
