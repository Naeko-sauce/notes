## 基本数据类型转换

* 自动转换

  > * 在Java程序进行赋值或者运算时，精度小的类型自动转换为精度大的数据类型，这个就是自动类型转换
  > * char==》int==》long==》float==》double
  > * byte==》short==》int==》long==》float==》double
  >
  > ```java
  > public class h5 {
  > 	public static void main(String[] args){
  > 		int d1 = 'a';//char -> int
  > 		double d2 = 80;//int - double
  > 		System.out.println(d1);
  > 		System.out.println(d2);
  > 	}
  > }
  > ```

* 自动转换细节

  > * 有多种类型的数据混合运算时，系统首先自动将所有数据转换成容量最大的那种数据类型，然后在进行计算
  > * 当把精度大的数据类型赋给精度小的数据类型时，就会报错，反之会进行自动类型转换。
  > * byte，short和char之间不会相互自动转换
  > * byte，short，char 他们三者可以计算，在计算时首先转换为int类型
  > * Boolean不参与自动类型转换
  > * 自动提升，表达式结果的类型自动提示为操作数中最大的类型

## 强制类型转换

* 强制类型转换

  > * 自动类型转换的逆过程，将容量大的数据类型转换为容量小的数据类型。使用时要加上强制转换符(),但是可能造成精度降低或者溢出 
  >
  > ```java
  > public class h5 {
  > 	public static void main(String[] args){
  > 		//把一个double类型的小数强制转换成int类型就会损失后面的小数点
  > 		int m1 = (int)1.9;
  > 		System.out.println(m1);
  > 		//如果强制把一个大类型的数转换成小类型就会造成精度溢出
  > 		int c1 = 900;
  > 		byte c2 = (byte)c1;
  > 		System.out.println(c2);
  > 	}
  > }
  > ```
  >
  > * 当进行数据的大小从大到小，就需要使用强制转换，强转符号只针对最近的操作数有效，往往会使用小括号提升优先级
  > * char类型可以保存 int的常量值，但是不能保存int的变量值，需要强转
  > * byte和short类型在进行运算时，当作int类型处理
  >
  > ```java
  > public class h5 {
  > 	public static void main(String[] args){
  > 		//把一个double类型的小数强制转换成int类型就会损失后面的小数点
  > 		int m1 = (int)1.9;
  > 		System.out.println(m1);
  > 		//如果强制把一个大类型的数转换成小类型就会造成精度溢出
  > 		int c1 = 900;
  > 		byte c2 = (byte)c1;
  > 		System.out.println(c2);
  > 		//强制转换符号只针对最近的操作数有效，往往会使用小括号提升优先级
  > 		//int x = (int)10*3.5+6;//会编译错误：因为这个最后结果是double类型
  > 		int x = (int)(10*3.5+6*1.5);//会先进行运算在转所以说是对的
  > 		System.out.println(x);
  > 	}
  > }
  > ```

## 基本数据类型和string类型的转换

* 数据类型和string类型转换

  > * 在开发中经常需要将基本数据类型转成string类型，或者将string类型转成基本数据类型。
  > * 基本类型转string类型：将基本类型的值加“ ”即可
  > * string类型转基本数据类型：通过基本类型的包装类调用parsexx方法
  >
  > ```java
  > public class h6 {
  > 	public static void main(String[] args){
  > 		//基本数据类型=> string
  > 		int a = 100;
  > 		float a1 = 1.1f;
  > 		double a2 = 4.1;
  > 		boolean a3 = true;
  > 		String b = a + "";
  > 		String b1 = a1 + "";
  > 		String b2 = a2 + "";
  > 		String b3 = a3 + "";
  > 		System.out.println(b + " " + b1 + " " + b2 + " " + b3);
  > 		//string转成基本数据类型
  > 		//使用基本数据类型对应的包装类，相应方法，得到基本数据类型
  > 		String a4 = "123";
  > 		int n = Integer.parseInt(a4);//将字符串转为int类型下面的以此类推
  > 		double n1 = Double.parseDouble(a4);
  > 		float n2 = Float.parseFloat(a4);
  > 		long n3 = Long.parseLong(a4);
  > 		byte n4 = Byte.parseByte(a4);
  > 		boolean n5 = Boolean.parseBoolean("true");
  > 		short n6 = Short.parseShort(a4);
  > 		System.out.println("===============");
  > 		System.out.println(n);
  > 		System.out.println(n1);
  > 		System.out.println(n2);
  > 		System.out.println(n3);
  > 		System.out.println(n4);
  > 		System.out.println(n5);
  > 		System.out.println(n6);
  > 		//怎么把字符串转成字符char-> 含义是指把字符串的第一个字符得到
  > 		//a4.charAt(0) 得到s4字符串的第一给字符
  > 		System.out.println(a4.charAt(0));
  > 	}
  > }
  > ```
  >
  > * 在将string类型转成基本数据类型时，要确保String类型能够转成有效的数据，比如可以把“123”，转成一个整数，但是不能把“hell”转成一个整数
  > * 如果格式不正确，就会抛出异常，程序就会终止

