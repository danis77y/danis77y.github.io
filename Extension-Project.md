import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.println("=================================================");
        System.out.println("  Welcome to the RPG Hero Arena Simulator!       ");
        System.out.println("=================================================");
        System.out.println("Prepare your character to face the dungeon arena.\n");

        System.out.print("Enter your Hero's name: ");
        String nameInput = scanner.nextLine();

        System.out.print("Choose a class (Warrior, Mage, Rogue): ");
        String classInput = scanner.nextLine();

        System.out.print("Enter difficulty level (1 = Easy, 2 = Medium, 3 = Hard): ");
        int difficultyInput = scanner.nextInt();

        Hero playerHero = new Hero(nameInput, classInput, difficultyInput);

        System.out.println("\n--- YOUR HERO HAS BEEN CREATED ---");
        playerHero.displayInfo();

        System.out.println("\n=================================================");
        System.out.println("A wild Dungeon Monster appears in the arena!");
        System.out.println("=================================================");

        int monsterAttack = 25 * difficultyInput;
        System.out.println("The monster attacks dealing " + monsterAttack + " raw damage!");

        int finalHealth = playerHero.getMaxHealth();
        int heroDefense = playerHero.getDefense();

        int damageTaken = monsterAttack - heroDefense;
        if (damageTaken < 0) {
            damageTaken = 0;
        }

        finalHealth = finalHealth - damageTaken;

        System.out.println(playerHero.getName() + " blocks " + heroDefense + " damage with defense.");
        System.out.println("Damage taken: " + damageTaken + " points.");

        System.out.println("\n--- COMBAT RESULT ---");
        
        if (finalHealth > 0) {
            System.out.println("🎉 CONGRATULATIONS!");
            System.out.println(playerHero.getName() + " survived the attack with " + finalHealth + " HP remaining!");
            System.out.println("You have defeated the monster and cleared the arena!");
        } else {
            System.out.println("💀 GAME OVER!");
            System.out.println(playerHero.getName() + " was overwhelmed by the monster's power.");
            System.out.println("Your health dropped to 0. Better luck next time!");
        }

        System.out.println("=================================================");
        
        scanner.close();
    }
}

// CLASE SECUNDARIA HERO (Agregada aquí mismo para evitar errores de carpetas)
class Hero { 
   
    private String name;
    private String heroClass;
    private int maxHealth;
    private int attackPower;
    private int defense;

    public Hero(String name, String heroClass, int difficulty) {
        this.name = name;
        this.heroClass = heroClass;
        this.maxHealth = calculateHealth(heroClass, difficulty);
        this.attackPower = calculateAttack(heroClass, difficulty);
        this.defense = calculateDefense(heroClass);
    }

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

    public void displayInfo() {
        System.out.println("\n=== " + name + " the " + heroClass + " ===");
        System.out.println("Health: " + maxHealth);
        System.out.println("Attack: " + attackPower);
        System.out.println("Defense: " + defense);
    }
}
