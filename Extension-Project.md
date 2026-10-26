public class Hero {
    // Instance variables
    private String name;
    private String heroClass;
    private int maxHealth;
    private int attackPower;
    private int defense;


    // Constructor
    public Hero(String name, String heroClass, int difficulty) {
        this.name = name;
        this.heroClass = heroClass;
        this.maxHealth = calculateHealth(heroClass, difficulty);
        this.attackPower = calculateAttack(heroClass, difficulty);
        this.defense = calculateDefense(heroClass);
    }


    // Calculate health based on class and difficulty
    private int calculateHealth(String heroClass, int difficulty) {
        if (heroClass.equals("Warrior")) {
            return 100 + (difficulty * 20);
        } else if (heroClass.equals("Mage")) {
            return 70 + (difficulty * 15);
        } else if (heroClass.equals("Rogue")) {
            return 80 + (difficulty * 18);
        } else {
            return 90 + (difficulty * 10);
        }
    }


    // Calculate attack power based on class and difficulty
    private int calculateAttack(String heroClass, int difficulty) {
        if (heroClass.equals("Warrior")) {
            return 15 + (difficulty * 3);
        } else if (heroClass.equals("Mage")) {
            return 20 + (difficulty * 4);
        } else if (heroClass.equals("Rogue")) {
            return 18 + (difficulty * 3);
        } else {
            return 12 + (difficulty * 2);
        }
    }


    // Calculate defense based on class
    private int calculateDefense(String heroClass) {
        if (heroClass.equals("Warrior")) {
            return 10;
        } else if (heroClass.equals("Mage")) {
            return 5;
        } else if (heroClass.equals("Rogue")) {
            return 7;
        } else {
            return 8;
        }
    }


    // Getters
    public String getName() {
        return name;
    }


    public String getHeroClass() {
        return heroClass;
    }


    public int getMaxHealth() {
        return maxHealth;
    }


    public int getAttackPower() {
        return attackPower;
    }


    public int getDefense() {
        return defense;
    }


    // Display hero info
    public void displayInfo() {
        System.out.println("\n=== " + name + " the " + heroClass + " ===");
        System.println("Health: " + maxHealth);
        System.out.println("Attack: " + attackPower);
        System.out.println("Defense: " + defense);
    }
} 

