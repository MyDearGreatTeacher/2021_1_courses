
#
```
package moreExtendDemo;

class CMath {
   public void getMax(int a, int b) {
      int bigNum;
      if (a > b)
         bigNum = a;
      else
          bigNum = b;
      System.out.println(a + " 與 " + b + " 的最大數為 " + bigNum);
   }
}

class SonCMath extends CMath {          // SonCMath繼承CMath類別
   public void getFactorial(int a) {
      int ans = 1, i;
      System.out.print(a + "! = ");
      for (i = 1; i < a; i++) {
         System.out.print(i + "*");
         ans *= i;
      }
      ans *= a;
      System.out.println(a + " = " + ans);
   }
}

class GrandSonCMath extends SonCMath {  //GrandSonCMath繼承SonCMath類別
   public void getFabonacci(int a) {
      int firstNum = 0, secondNum = 1;
      System.out.print("費氏數列：") ;
      System.out.print(firstNum + ", " +secondNum);
      int ans;
      for(int i=2; i<=a; i++) {
         ans = firstNum + secondNum;
         System.out.print(", " +ans);
         firstNum = secondNum;
         secondNum = ans;
      }
   }
}

public class MoreExtendDemo {
	public static void main(String[] args) {
		CMath math0 = new CMath();
		math0.getMax(10, 20); 
		
		SonCMath math1 = new SonCMath();
		math1.getMax(10, 20);     // 呼叫子類別繼承父類別的方法
		System.out.println();
		math1.getFactorial(5);    // 呼叫子類別自己的方法
		
		GrandSonCMath math2 = new GrandSonCMath();
		math2.getMax(10,20);        //呼叫繼承自祖父類別的方法
		math2.getFactorial(5);      //呼叫繼承自祖父類別的方法
		math2.getFabonacci(10);     //呼叫用自已的方法
	}
}

```

###

```
public class Fibonacci {

	public static void main(String[] args) {
		
		/*
		 * Write a program to find first 20 numbers of Fibonacci Series
		 * 0 1 1 2 3 5 8 13 21
		 */
		int num1 = 0;
		int num2 = 1;
		int num3 = 0;
		
		System.out.println(num1);
		System.out.println(num2);
		
		for(int i = 1; i <= 18; i++) {
			num3 = num1 + num2;
			System.out.println(num3);
			num1 = num2;
			num2 = num3;
		}
		

	}

}
```
```

```
