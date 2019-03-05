# Cosine-Law-Calcpackage Assignment1;

import java.util.InputMismatchException;
import java.util.Scanner;

public class CosinelawCalc {
	public static int NaN = 0;
	//make  a scanner object	
	// it doesn't hold anything at this point
	static Scanner scan = new Scanner(System.in);

	/* say function
	 * output a string msg to the console
	 */
	public static void say(String msg) {
		System.out.println(msg);
	}

	/* ask function double
	 * output a prompt to the user
	 * get a valid input from the user
	 * return that value as a double
	 */
	public static double ask(String prompt) {
		say (prompt);
		double value = -99;
		while (value == -99) {
			//try to get a good number
			try {
				value = scan.nextDouble();
			}
			catch(InputMismatchException error) {
				//failing that, ask again
				scan.next();//this is to clear out the enter character from the error
				//error.printStackTrace();
				say("You were supposed to type in 1 or 2!");
			}
			catch(ArrayIndexOutOfBoundsException e) {

			}
			catch (Exception e) {
				say("Invalid Response");
			}

		return value;
	}
		return value;
	}


	public static double cos (double input) {
		// convert Angle to Radian measure
		return Math.acos(Math.toRadians(input));
}
	public static double acos (double input) {
		//convert Angle to Degree measure
		return Math.toDegrees(Math.acos(input));
	}
	//calcAngle function
	//put function CalcAngle here (calculates the angle given the side lengths)
	public static void CalcAngle (double a, double b, double c) {
		double angle = Double.NaN;
		 angle = (Math.acos(((a * a) + (b * b) - (c * c)) / (2 * b * a)));
		say("The angle of your triangle is " + angle/Math.PI*180.0 + " degrees");
		if (angle == NaN) {
			say("Whooops! Wrong Numbers. It's annoying but please try again!!");
		}
	}

	//calcSide function
	//put calcSide function here (calculates the side length gives to sides and an angle)
	public static void CalcSide (double _a, double _b, double angleC) {

		double answer = Double.NaN;
		answer = (Math.sqrt((_a * _a) + (_b + _b) - 2 * _a * _b * Math.cos(angleC*Math.PI/180.0)));
		
		if (answer == NaN) {
			say("Whooops! Wrong Numbers. It's annoying but please try again!!");
		}	
		say("The side1 of your triangle is " + answer + " meters");
		
	}

	//askBool function
	/* output a string prompt to the user
	 * get a y/n reply from the user
	 * based on what the reply is, return the boolean
	 */
	public static boolean askBool(String prompt) {
		say (prompt);
		String reply = scan.next();
		//check to see if reply was yes
		if(reply.contains("y")) {
			return true;
		}
		return false;
	}
	
	public static void main(String[] args) {
		//this determines whether the program repeats	
		boolean cont = true; 	
		//give a welcome message and ask what they want to calculate
		say("Hello and Welcome! This program will calculate the side or angle of a triangle.");
		while(cont == true) {
			double menuSelection = ask("Do you want to calc the angle (1) or side length (2) of the triangle?");

			//check menuSelection to call either CalcAngle or CalcSide
			if (menuSelection == 1) {
				double a = ask("Please enter a positive,non-zero number, for side a, adj to the angle, in meters");
				double b = ask("Please enter a positive non-zero number, for side b, adj to the angle, in meters");
				double c = ask("Please enter a positive,non-zero number, for side c, opp to the angle, in meters");
				CalcAngle(a, b, c); 
			}

			else if (menuSelection == 2) {
				double _a = ask ("Please enter a positive,non-zero number, for side a, adj to the angle, in meters");
				double _b = ask ("Please enter a positive,non-zero number, for side b, adj to the angle, in meters");
				double AngleC = ask("Please enter a positive,non-zero number, for angleC in bet. side1 & side3, in degrees");
				CalcSide(_a, _b, AngleC);
			}


			else {
				say("Not a valid option, Enter either 1 or 2");
			}
		

			cont = askBool("Do you want to continue? (y/n)");
			//end while
			//java wants to close the scanner object do this
			
		}
	}
}




