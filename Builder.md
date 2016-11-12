```
public class User {

	String firstName;
	String lastName;
	String phone;
	String address;
	int age;
	
	// No default constructor
//	public User () {}
	
	/**
	 * Why private? Encourage the use of Builder class
	 * @param builder
	 */
	private User(UserBuilder builder) {
		/**
		 * Any variable could be or not be here
		 */
		this.firstName = builder.firstName;
		this.lastName = builder.lastName;
		this.age = builder.age;
		this.phone = builder.phone;
		this.address = builder.address;
	}
	
	public static void main(String[] args) {
		// Problems with this normal program:
		//		User user1 = new User("Master", "Lv");
		//		user1.age = 5;
		
		/**
		 * When will this object be "complete"? If we try to access "age" now, we may get null
		 * Builder pattern: Once the object is created, 
		 */
		// 1. One line
		User user2 = new User.UserBuilder("First","Last").age(25).address("My address").phone("412-537-2008").build();
		
		// 2. Separate
		User.UserBuilder builder = new User.UserBuilder("first", "last");
		builder.age(25);
		builder.address("My address");
		builder.phone("412-537-2008");
		User user3 = builder.build();
		
	}
	
	/**
	 * Static nested class (not a non-static inner class)
	 * @author Phoenix
	 */
	// With "static", UserBuilder will not be object-dependable
	// With "public", Buildercan be accessed outside, instead of User class
	public static class UserBuilder {
		/**
		 * final fields are required
		 */
		private final String firstName; // final = required
		private final String lastName;  // final = required
		private String phone;
		private String address;
		private int age;
		
		public UserBuilder (String firstName, String lastName) {
			this.firstName = firstName;
			this.lastName = lastName;
		}
		
		public User build() {
			return new User(this);
		}
		
		public UserBuilder phone(String phone) {
			this.phone = phone;
			return this;
		}

		public UserBuilder address(String address) {
			this.address = address;
			return this;
		}

		public UserBuilder age(int age) {
			this.age = age;
			return this;
		}
		
	}
	
}
```
