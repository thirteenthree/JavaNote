#### m2方法需要等待m1执行完再执行吗
```Java
public class ThreadTest
{
	public static void main(String[] args) throws Exception{

		MyClass mc = new MyClass();

		Processor p = new Processor(mc);

		Thread t1 = new Thread(p);
		t1.setName("t1");
		Thread t2 = new Thread(p);
		t2.setName("t2");

		//启动线程
		t1.start();

		//延迟(保证t1线程先启动，并执行run)
		Thread.sleep(1000);

		t2.start();

	}
}

class Processor implements Runnable
{
	MyClass mc;

	Processor(MyClass mc){
		this.mc = mc;
	}

	public void run(){
		
		if(Thread.currentThread().getName().equals("t1")){
			mc.m1();
		}
		
		if(Thread.currentThread().getName().equals("t2")){
			mc.m2();
		}

	}
}

class MyClass
{
	public synchronized void m1(){

		//休眠
		try{
			Thread.sleep(10000);
		}catch(Exception e){}
		
		System.out.println("m1....");
	}
	
	/*
	//m2方法的执行不需要等m1的结束，因为m2方法上没有synchronized
	public void m2(){
		System.out.println("m2....");
	}
	*/
	
	//m2方法会等m1方法结束，t1,t2共享同一个mc,并且m1和m2方法上都有synchronized
	public synchronized void m2(){
		System.out.println("m2....");
	}
}
```







#### m1方法与m2方法会相互等待吗?

```Java
public class ThreadTest
{
	public static void main(String[] args) throws Exception{

		MyClass mc1 = new MyClass();
		MyClass mc2 = new MyClass();

		Processor p1 = new Processor(mc1);
		Processor p2 = new Processor(mc2);

		Thread t1 = new Thread(p1);
		t1.setName("t1");
		Thread t2 = new Thread(p2);
		t2.setName("t2");

		//启动线程
		t1.start();

		//延迟(保证t1线程先启动，并执行run)
		Thread.sleep(1000);

		t2.start();

	}
}

class Processor implements Runnable
{
	MyClass mc;

	Processor(MyClass mc){
		this.mc = mc;
	}

	public void run(){
		
		if(Thread.currentThread().getName().equals("t1")){
			mc.m1();
		}
		
		if(Thread.currentThread().getName().equals("t2")){
			mc.m2();
		}

	}
}

class MyClass
{
	public synchronized void m1(){

		//休眠
		try{
			Thread.sleep(10000);
		}catch(Exception e){}
		
		System.out.println("m1....");
	}
	
	//m2方法不会等m1方法结束，t1,t2不共享同一个mc
	public synchronized void m2(){
		System.out.println("m2....");
	}
}
```









#### 类锁

```Java
/*
	类锁,类只有一个，所以锁是类级别的，只有一个.
*/
public class ThreadTest
{
	public static void main(String[] args) throws Exception{	
		Thread t1 = new Thread(new Processor());
		Thread t2 = new Thread(new Processor());

		t1.setName("t1");
		t2.setName("t2");

		t1.start();
		//延迟，保证t1先执行
		Thread.sleep(1000);
		t2.start();

	}
}
class Processor implements Runnable
{
	public void run(){
		if("t1".equals(Thread.currentThread().getName())){
			MyClass.m1();
		}

		if("t2".equals(Thread.currentThread().getName())){
			MyClass.m2();
		}
	}
}
class MyClass
{
	//synchronized添加到静态方法上，线程执行此方法的时候会找类锁。
	public synchronized static void m1(){
		try{
            Thread.sleep(10000);
        }catch(Exception e){}
		System.out.println("m1....");
	}

	//不会等m1结束，因为该方法没有被synchronized修饰
	/*
	public static void m2(){
		System.out.println("m2...");
	}
	*/

	//m2方法等m1结束之后才能执行，该方法有synchronized
	//线程执行该代码需要“类锁”，而类锁只有一个。
	public synchronized static void m2(){
		System.out.println("m2...");
	}
}
```

