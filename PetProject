// Manjit Singh
// Pet Project Program. Makes a Pet that the user can Name, Feed, play with and have survive as long as possible
import java.util.Scanner; // Needed to make scanner available
import java.util.Random; // Needed to make random available
// Creates a class Pet with Hunger, Fun and Energy
class Pet{
    String Name;
    int Hunger;
    int Fun;
    int Energy;
}
// class used to return multiple things
class Returner{
    Pet pet;
    int[] Miniarray;
    String petName;
}
// The main class with all the methods
public class petProject {
    public static void main(String[] args) {
        int[] DaysArray = {0,0,0,0,0};
        String[] petName = new String[5];
        Pet pet = new Pet();
        Pet[] List = Arrays();
        StartMessage();
        Returner terine = MainMenu(List, pet, DaysArray, petName);
        int[] MiniArray = terine.Miniarray;
        petName[MiniArray[1]] = terine.petName;
        DaysArray[MiniArray[1]] = MiniArray[0];
        int i = MiniArray[1];
        DeathMessage(DaysArray, List, i);
    }
    // Creates a new pet with Stats of 10 in everything
    public static Pet petDetails(String[] petName, int i, Pet[] List) {
        if(List[i]!= null){
            createPet(petName,List[i].Hunger,List[i].Fun,List[i].Energy, i);
            return List[i];
        }
        else {
            int[] StatsArray = createPet(petName, 10, 10, 10, i);
            Pet Temp = new Pet();
            Temp.Hunger = StatsArray[0];
            Temp.Fun = StatsArray[1];
            Temp.Energy = StatsArray[2];
            List[i] = Temp;
            return List[i];
        }
    }
    //Creates a new Pet Array of 5 Length
    public static Pet[] Arrays(){
        return new Pet[5];
    }
    // Start message that displays when you run the code
    public static void StartMessage(){
        System.out.println();
        System.out.println("This is a game where you have a pet.");
        System.out.println("Your Pet will start with 10 points in 3 categories. Fullness, Fun, Energy.");
        System.out.println("The maximum amount of points in any category is 20.");
        System.out.println("You can choose what to do with them that day e.g. Feed them, Play with them or let them sleep");
        System.out.println("Every time you do one of those actions, the corresponding stat will increase by up to 3");
        System.out.println("Every day that passes, decreases the other 2 stats. If any stat ever reaches 0. Well...");
        System.out.println("Let's just say you pet won't be \"Playing\" with your pet anymore.");
        System.out.println();
    }
    // Asks the user to choose a save state, Shows all save files and whether they contain something.
    public static Returner MainMenu(Pet[] List, Pet x, int[] Days, String[] petName){
        Scanner scanner = new Scanner(System.in);
        System.out.println("Choose your Pet:");
        Pet pet;
        for(int i = 0; i<5; i++){
            if (List[i] != null) {
                System.out.println((i+1)+ ". " + petName[i]);
            }
            else{
                System.out.println((i+1)+ ". Empty Pet File");
            }
        }
        System.out.println("6. Exit");
        int i = (scanner.nextInt()-1);
        if(i == 5){
            System.exit(0);
        }
        if (List[i] == null){
            petName[i] = Asker("What would you like to name your pet?");
            pet = petDetails(petName, i, List);
            List[i] = pet;
            PrintStats(Days, List, i);
            Days[i] = WhileLoop(Days, List, i, petName);
        }
        else if (List[i]!= null){
            PrintStats(Days, List, i);
            petDetails(petName, i, List);
            Days[i] = WhileLoop(Days, List, i, petName);
        }
        int[] MiniArray = new int[2];
        MiniArray[0] = Days[i];
        MiniArray[1] = i;
        Returner terine = new Returner();
        terine.pet = x;
        terine.Miniarray = MiniArray;
        terine.petName = petName[i];
        return terine;
    }
    // This method prints out the day along with all the current stats of the pet.
    public static void PrintStats(int[] Days, Pet[] List, int i){
        System.out.println("Day: " + Days[i]);
        System.out.println("Fullness: "+ List[i].Hunger);
        System.out.println("Fun: "+ List[i].Fun);
        System.out.println("Energy: " + List[i].Energy);
    }
    // This is the DeathMessage printed out after you lose. It changes based on how your pet died.
    public static void DeathMessage(int[] Days, Pet[] List, int i){
        if(List[i].Hunger <= 0){
            List[i].Hunger = 0;
            System.out.println("All your pet's have " + "died of hunger.");
        }
        else if(List[i].Fun <= 0){
             List[i].Fun = 0;
            System.out.println("All your pet's have " + "died of boredom.");
        }
        else if(List[i].Energy <= 0){
            List[i].Energy = 0;
            System.out.println("All your pets have " + "died of exhaustion.");
        }
        int counter = 0;
        for(int z = 0; z<5; z++){
            counter += Days[z];
        }
        System.out.println("Your pets managed to survive " + counter + " days.");
    }
    // Runs a while loop if none of the stats are 0, It asks what to do to the pet. Depending on the input, it increases
    // a stat whilst decreasing the other 2. If any stat ever exceeds 20 or goes below 0, it sets those values to 20 and
    // 0 respectively. It increments the days and runs the PrintStats method. It also prints out a message if any stat
    // ever exceeds its maximum value of 20. It then returns the value of Days.
    public static int WhileLoop(int[] Days, Pet[] List, int i, String[] petName) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();
        while (List[i].Hunger > 0 && List[i].Fun > 0 && List[i].Energy > 0) {
            if(List[i].Hunger <= 0 || List[i].Fun <= 0 || List[i].Energy <=0){
                break;
            }
            System.out.println("What would you like to do to your pet? (Feed, Play, Sleep, Exit)");
            String input = scanner.nextLine();
            if (List[i].Hunger < 20 && input.equals("Feed") || List[i].Hunger < 20 && input.equals("feed")) {
                List[i].Hunger = List[i].Hunger + random.nextInt(3) + 1;
                List[i].Fun = List[i].Fun - random.nextInt(2) - 1;
                List[i].Energy = List[i].Energy - random.nextInt(2) - 1;
                if (List[i].Hunger >= 20) {
                    List[i].Hunger = 20;
                } else if (List[i].Fun < 0) {
                    List[i].Fun = 0;
                } else if (List[i].Energy < 0) {
                    List[i].Energy = 0;
                }
                Days[i]++;
                PrintStats(Days, List, i);
            } else if (List[i].Fun < 20 && input.equals("Play") || List[i].Fun < 20 && input.equals("play")) {
                List[i].Fun = List[i].Fun + random.nextInt(3) + 1;
                List[i].Hunger = List[i].Hunger - random.nextInt(2) - 1;
                List[i].Energy = List[i].Energy - random.nextInt(2) - 1;
                if (List[i].Fun >= 20) {
                    List[i].Fun = 20;
                } else if (List[i].Hunger < 0) {
                    List[i].Hunger = 0;
                } else if (List[i].Energy < 0) {
                    List[i].Energy = 0;
                }
                Days[i]++;
                PrintStats(Days, List, i);
            } else if (List[i].Energy < 20 && input.equals("Sleep") || List[i].Energy < 20 && input.equals("sleep")) {
                List[i].Energy = List[i].Energy + random.nextInt(3) + 1;
                List[i].Fun = List[i].Fun - random.nextInt(2) - 1;
                List[i].Hunger = List[i].Hunger - random.nextInt(2) - 1;
                if (List[i].Energy >= 20) {
                    List[i].Energy = 20;
                } else if (List[i].Hunger < 0) {
                    List[i].Hunger = 0;
                } else if (List[i].Fun < 0) {
                    List[i].Fun = 0;
                }
                Days[i]++;
                PrintStats(Days, List, i);
            } else if(input.equals("Exit")){
                MainMenu(List, List[i], Days, petName);
            }
            else if (List[i].Hunger >= 20) {
                System.out.println("The maximum amount of stat points in 1 category is 20. Try a different command");
            } else if (List[i].Fun >= 20) {
                System.out.println("The maximum amount of stat points in 1 category is 20. Try a different command");
            } else if (List[i].Energy >= 20) {
                System.out.println("The maximum amount of stat points in 1 category is 20. Try a different command");
            }
            else if (input.equals("Cheat")) {
                System.out.println("Now increasing all stats by up to 6");
                for (int b = 0; b < 2; b++) {
                    List[i].Hunger = List[i].Hunger + random.nextInt(3) + 1;
                    List[i].Fun = List[i].Fun + random.nextInt(3) + 1;
                    List[i].Energy = List[i].Energy + random.nextInt(3) + 1;
                }
            }else {
                System.out.println("That's an invalid input.");
            }
        }
        return Days[i];
    }
    // Basic method that takes in a string, outputs it and returns the result inputted by the user
    public static String Asker(String Question){
        Scanner scanner = new Scanner(System.in);
        System.out.println(Question);
        return scanner.nextLine();
    }
    // Store values in each section of the record. Hunger, Fun, Energy.
    public static int[] createPet(String[] petName, int Hunger, int Fun, int Energy, int i){
        Pet x = new Pet();
        x = SetPetInfo(x, petName, Hunger, Fun, Energy, i);
        Hunger = GetHunger(x);
        Fun = GetFun(x);
        Energy = GetEnergy(x);
        return new int[]{Hunger,Fun,Energy};
    }

    // Store values in each section of the record. Hunger, Fun, Energy.
    public static Pet SetPetInfo(Pet x, String[] petName, int Hunger, int Fun, int Energy, int i){
        x.Name = petName[i];
        x.Hunger = Hunger;
        x.Fun = Fun;
        x.Energy = Energy;
        return x;
    }
    public static int GetHunger(Pet x){
        return x.Hunger;
    }
    public static int GetFun(Pet x){
        return x.Fun;
    }
    public static int GetEnergy(Pet x){
        return x.Energy;
    }
}
