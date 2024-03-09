## Lab Report 5 - Debugging
</br>

**Student post** \
<img width="438" alt="Screenshot 2024-03-09 at 1 29 21 PM" src="https://github.com/miachen67/cse15l-lab-reports/assets/147332750/6ca7c410-fe15-4a06-a852-a96a48668d1b"> \
I am getting a failure in my test cases when I test my findMax method on an argument array that only consists of negative numbers.  My failure-inducing input is the array [-1, -2, -3, -4, -5, -6].

**TA Response** \
It looks like your findMax method is returning 0 even though there is no 0 in your input array. When is a case where your findMax method returns 0? 

**Student's Fixed Output** \
<img width="245" alt="Screenshot 2024-03-09 at 1 39 52 PM" src="https://github.com/miachen67/cse15l-lab-reports/assets/147332750/32917353-adec-43ea-856b-866e65208afb"> \
The bug was setting `int max = 0` at the beginning, rather than `Integer.MIN_VALUE`. This is because if all of the elements in the input array were negative, none would be greater than 0 and as a result, 0 would be the max. You could also fix this by setting int max to equal the first element of the array.


</br> 

## Code Setup
**The file & directory structure needed**
```
- lib
  - hamcrest-core-1.3.jar
  - junit-4.13.2.jar
- Tester.java
- findMax.java
- test.sh
```
**The contents of each file before fixing the bug**
Tester.java's contents: 
```
import static org.junit.Assert.*;
import org.junit.Test;
import java.util.Arrays;

public class Tester {
  @Test
  public void testPositive() {
    int[] arr = new int[]{1, 2, 3, 4, 5, 6};
    assertEquals(6, findMax.findMax(arr));
  }
  @Test
  public void testNegativesAndPos() {
    int[] arr = new int[]{-1, 2, 3, -4, 6};
    assertEquals(6, findMax.findMax(arr));
  }

  @Test
  public void testAllNegatives() {
    int[] arr = new int[]{-1, -2, -3, -4, -5};
    assertEquals(-1, findMax.findMax(arr));
  }
}
```

test.sh's contents: 
```
javac -g -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore Tester
```

findMax.java's contents:
```
public class findMax{
    public static int findMax(int[] arr){
        int max = Integer.MIN_VALUE;
        for (int i = 0; i < arr.length; i++){
            if (arr[i] > max){
                max = arr[i];
            }
        }
        return max;
    }
}
```

**The full command line (or lines) you ran to trigger the bug**
`bash test.sh` is the command that triggered the bug, specifically when the testAllNegatives test was run in my tester file.
**A description of what to edit to fix the bug**
The bug was setting `int max = 0` at the beginning, rather than `Integer.MIN_VALUE`. This is because if all of the elements in the input array were negative, none would be greater than 0 and as a result, 0 would be the max. You could also fix this by setting int max to equal the first element of the array.
