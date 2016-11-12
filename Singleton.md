Ensure a class has only one instance and provide a global point of access to it.  
Why? There's only one instance exists or it comsumes too much resources and we cannot afford two.  

Know how to write code!  
```
public class Singleton {

	private static final Singleton INSTANCE = new Singleton();
	
	private Singleton() {};
	
	public static Singleton getInstance() {
		return INSTANCE;
	}
	
}
```
