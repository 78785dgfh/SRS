class Animal {
    protected String name;
    protected double speedRun;
    protected double speedSwim;
    protected int endurance;
    public Animal(String name, double speedRun, double speedSwim, int endurance) {
        this.name = name;
        this.speedRun = speedRun;
        this.speedSwim = speedSwim;
        this.endurance = endurance;
    }
    public double run(int distance) {
        int cost = distance;
        return performAction(distance, cost, speedRun, "бег");
    }
    public double swim(int distance) {
        return -1;
    }
    protected double performAction(int distance, int cost, double speed, String action) {
        if (endurance < cost) {
            System.out.println(name + " устал(а) и не может " + action + ".");
            return -1;
        }
        endurance -= cost;
        double time = distance / speed;
        System.out.println(name + " потратил(а) " + time + " секунд(ы) на " + action + ".");
        return time;
    }
    public void info() {
        System.out.println("Имя: " + name + ", Выносливость: " + endurance);
    }
}
class Cat extends Animal {
    public Cat(String name, double speedRun, int endurance) {
        super(name, speedRun, 0, endurance);
    }
    @Override
    public double swim(int distance) {
        System.out.println(name + " не умеет плавать.");
        return -1;
    }
}
class Dog extends Animal {
    public Dog(String name, double speedRun, double speedSwim, int endurance) {
        super(name, speedRun, speedSwim, endurance);
    }

    @Override
    public double swim(int distance) {
        int cost = distance * 2;
        return performAction(distance, cost, speedSwim, "плавание");
    }
}
class Horse extends Animal {
    public Horse(String name, double speedRun, double speedSwim, int endurance) {
        super(name, speedRun, speedSwim, endurance);
    }
    @Override
    public double swim(int distance) {
        int cost = distance * 4; 
        return performAction(distance, cost, speedSwim, "плавание");
    }
}
public class Main {
    public static void main(String[] args) {
        Cat cat = new Cat("Мурка", 10, 15);
        Dog dog = new Dog("Шарик", 12, 5, 20);
        Horse horse = new Horse("Гарри", 15, 3, 30);

        cat.run(5);
        cat.swim(5);
        cat.info();

        dog.run(10);
        dog.swim(5);
        dog.info();

        horse.run(20);
        horse.swim(10);
        horse.info();
    }
}
