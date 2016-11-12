## Abstract Factory
##### Layers/complexity:
1. Family manufacturer: One method for each component (like this)
2. Local factory: One class for each component 
3. Modern factory: Multiple classes for each component

```
/**
 * Factory method - factory class - abstract factory
 * Factory method: easy, single purpose
 * Factory class: medium, one group/kind of product(room)
 * Abstract factory: complex, many different kinds of products (button, window, bar...) 
 * @author Phoenix
 */
public class AbstractFactory {}

interface RoomFactory {
	public Room makeRoom();
}

class OrdinaryRoomFactory implements RoomFactory {
	
	@Override
	public Room makeRoom() {
		return new OrdinaryRoom();
	}
}

class MagicRoomFactory implements RoomFactory {
	
	@Override
	public Room makeRoom() {
		return new MagicRoom();
	}
}

class MazeGame2 {
	private final RoomFactory factory;
	public MazeGame2(RoomFactory factory) {
		this.factory = factory;
	}
	
	void createGame() {
		Room r1 = factory.makeRoom();
		Room r2 = factory.makeRoom();
	}
}

```
## Maze game
A creational pattern for creating new objects
Separate out the object creation logic and delegate it to factory class or method
```
public class MazeGame {
	public void createGame() {
		Room room1 = makeRoom();
		Room room2 = makeRoom();
		room1.connect(room2);
		this.addRoom(room1);
		this.addRoom(room2);
	}
	
	// Factory method
	protected Room makeRoom() {
		return new OrdinaryRoom();
	}
	public void addRoom(Room room){}
	
	
	public static void main(String[] args) {
		MazeGame game1 = new MazeGame();
		game1.makeRoom(); // make two ordinary rooms
		MagicMazeGame game2 = new MagicMazeGame();
		game2.makeRoom(); // make two magic rooms
	}
}


class MagicMazeGame extends MazeGame {
	@Override
	protected Room makeRoom() {
		return new MagicRoom();
	}
}

class Room {
	public void connect(Room room) {}
}
class OrdinaryRoom extends Room {}
class MagicRoom extends Room {}
```
