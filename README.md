# Lab-8_202001180

# Unit Testing with JUnit

## Goal:
The goal of this lab is to learn how to use JUnit to write unit tests for Java programs.

# Lab Exercises

1. Created a new Eclipse project - vsnlab8 and within that created a package - vsnlab8
![image](https://user-images.githubusercontent.com/124247649/233311221-4db5a798-8deb-45ba-a4c7-17133d2c0b57.png)

2. Created a class in the package - class name - Boa and junit test case file - BoaTest

<pre>
package vsnlab8;

public class Boa {
	private String name;
	private int length; // the length of the boa, in feet
	private String favoriteFood;
	
	public Boa (String name, int length, String favoriteFood){
		this.name = name;
		this.length = length;
		this.favoriteFood = favoriteFood;
	}
	// returns true if this boa constrictor is healthy
	public boolean isHealthy(){
		return this.favoriteFood.equals("granola bars");
	}
	
	// returns true if the length of this boa constrictor is
	// less than the given cage length
	public boolean fitsInCage(int cageLength){
		return this.length < cageLength;
	}
  }
</pre>

![image](https://user-images.githubusercontent.com/124247649/233313522-6a13c581-3090-4fd3-b2d0-0cbee92fdc2e.png)


3. Created junit test case for class Boa - BoaTest and for test method stubs, select both isHealthy() and fitsInCage(int).

4. Added unit tests - 

Method annotated with @Before will be run before each test executes.

<pre>
package vsnlab8;

import static org.junit.Assert.*;

import org.junit.Before;
import org.junit.Test;

public class BoaTest {
	
	private Boa jen;
	private Boa ken;

	@Before
	public void setUp() throws Exception {
		//initialization
		jen = new Boa("Jennifer", 2, "grapes");
		ken = new Boa ("Kenneth", 3, "granola bars");
	}
}
</pre>

![image](https://user-images.githubusercontent.com/124247649/233314800-85dfa15a-238e-4a64-89e5-3de731dd1dd5.png)

5. Added private fields for jen and ken in the Boa class.

<pre>
private Boa jen;
private Boa ken;
</pre>

We added private fields for jen and ken to the BoaTest class, and initialized them in the setUp method. We also updated the testIsHealthy and testFitsInCage methods to use these Boa objects for testing.

Note that the setUp method will be executed before each test method, so any changes made to the Boa objects during a test will not affect the objects used in other tests.

![image](https://user-images.githubusercontent.com/124247649/233315307-b079b9d7-1021-4d04-a1c9-0e1e7afd0204.png)


6. Adding some test cases -
Modified code -

Method annotated with @Test will be run but the order is not guaranteed.

<pre>
package vsnlab8;

import static org.junit.Assert.*;

import org.junit.Before;
import org.junit.Test;

public class BoaTest {
	
	private Boa jen;
	private Boa ken;

	@Before
	public void setUp() throws Exception {
		//initialization
		jen = new Boa("Jennifer", 2, "grapes");
		ken = new Boa ("Kenneth", 3, "granola bars");
	}

	@Test 
	public void testIsHealthy() {
		//testing isHealthy for 2 objects
		assertEquals(false,jen.isHealthy());
		assertEquals(true,ken.isHealthy());
	}
	
	@Test 
	public void testFitsInCage() {
		//testing isHealthy for 2 objects		
		assertEquals(false,jen.fitsInCage(1)); // less than the size of cage
		assertEquals(false,jen.fitsInCage(2)); // equal to the size of cage		
		assertEquals(true,jen.fitsInCage(3)); // greater than the size of cage
	}
}
</pre>

![image](https://user-images.githubusercontent.com/124247649/233316038-4f6cb845-2333-4668-8bbe-aa44cb34badf.png)

* In the first test case, we're testing the isHealthy method of the Boa class. We create two Boa objects with different favorite foods, and verify that isHealthy returns false for the first object and true for the second object.

* In the second test case, we're testing the fitsInCage method of the Boa class. We create three Boa objects with different lengths, and test whether they fit in cages of different lengths.

7. Running the two test cases - isHealthy() and fitsInCage()

![image](https://user-images.githubusercontent.com/124247649/233316402-cc5d4c5e-a507-44f0-a08c-99fa8df7c981.png)

8. Adding a new method to the Boa class -
Modified code -

<pre>
package vsnlab8;

public class Boa {
	private String name;
	private int length; // the length of the boa, in feet
	private String favoriteFood;
	
	public Boa (String name, int length, String favoriteFood){
		this.name = name;
		this.length = length;
		this.favoriteFood = favoriteFood;
	}
	// returns true if this boa constrictor is healthy
	public boolean isHealthy(){
		return this.favoriteFood.equals("granola bars");
	}
	
	// returns true if the length of this boa constrictor is
	// less than the given cage length
	public boolean fitsInCage(int cageLength){
		return this.length < cageLength;
	}
	public int lengthInInches()
	{
		int LengthInInches=this.length*12;
		return LengthInInches;
	}
	
}
</pre>

![image](https://user-images.githubusercontent.com/124247649/233316800-2450986a-c7e5-4bed-a0c0-7f8a9bf8ebcb.png)

9. Adding test cases for it -

Modified code -

<pre>
package vsnlab8;

import static org.junit.Assert.*;

import org.junit.Before;
import org.junit.Test;

public class BoaTest {
	
	private Boa jen;
	private Boa ken;

	@Before
	public void setUp() throws Exception {
		//initialization
		jen = new Boa("Jennifer", 2, "grapes");
		ken = new Boa ("Kenneth", 3, "granola bars");
	}

	@Test 
	public void testIsHealthy() {
		//testing isHealthy for 2 objects
		assertEquals(false,jen.isHealthy());
		assertEquals(true,ken.isHealthy());
	}
	
	@Test 
	public void testFitsInCage() {
		//testing isHealthy for 2 objects		
		assertEquals(false,jen.fitsInCage(1)); // less than the size of cage
		assertEquals(false,jen.fitsInCage(2)); // equal to the size of cage		assertEquals(true,jen.fitsInCage(3)); // greater than the size of cage
}
	@Test
	public void testlengthInInches()
	{
		assertEquals(24,jen.lengthInInches());
		assertEquals(36,ken.lengthInInches());
	}

}
</pre>

![image](https://user-images.githubusercontent.com/124247649/233317086-f4832bb8-fef1-4cde-b365-1d5e0e4f4199.png)


10. Running the test cases - 

![image](https://user-images.githubusercontent.com/124247649/233317159-c7b4eeb4-4d83-44bd-bc7a-d8204e141745.png)

