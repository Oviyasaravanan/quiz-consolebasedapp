import java.util.Scanner;
public class Quiz {
    public static void main(String[] args) {
        QuizImpl quiz = new QuizImpl();
        System.out.println("Welcome to the Quiz!\nChoose your difficulty level: Easy, Medium, or Hard");
        Scanner scanner = new Scanner(System.in);
        String selectedDifficulty = scanner.nextLine();
        quiz.start(selectedDifficulty);
    }
}
abstract class Ques {
    protected String ques;
    protected String[] options;
    protected int ans;
    public Ques(String q,String[] o,int a) {
        ques=q;
        options=o;
        ans=a;
    }
    public abstract boolean check(int userAns);
    public void display() {
        System.out.println(ques);
        for (int i=0;i<options.length;i++) {
            System.out.println((i+1)+". "+options[i]);
        }
    }
    public String[] getOptions() {
        return options;
    }

    public String getCorrect() {
        return options[ans];
    }
}
class EasyQues extends Ques {
    public EasyQues(String q, String[] o, int a) {
        super(q, o, a);
    }
    @Override
    public boolean check(int userAns) {
        return userAns == ans;
    }
}
class MediumQues extends Ques {
    public MediumQues(String q,String[] o,int a) {
        super(q,o,a);
    }
    @Override
    public boolean check(int userAns) {
        return userAns==ans;
    }
}
class HardQues extends Ques {
    public HardQues(String q,String[] o,int a) {
        super(q,o,a);
    }
    @Override
    public boolean check(int userAns) {
        return userAns==ans;
    }
}
interface QuizInterface {
    void start(String difficulty);
}
class QuizImpl implements QuizInterface {
    private Ques[] easyQues;
    private Ques[] mediumQues;
    private Ques[] hardQues;
    private int score = 0;
    public QuizImpl() {
        initializeQues();
    }

    private void initializeQues() {
        easyQues=new Ques[]{
                new EasyQues("Capital of France?", new String[]{"Paris", "Rome", "Berlin", "Madrid"}, 0),
                new EasyQues("Chemical symbol for water?", new String[]{"H2O", "CO2", "O2", "H2SO4"}, 0)
        };
        mediumQues = new Ques[]{
                new MediumQues("Planet known as the Red Planet?", new String[]{"Venus", "Mars", "Jupiter", "Saturn"}, 1),
                new MediumQues("Largest mammal?", new String[]{"Elephant", "Blue Whale", "Giraffe", "Hippopotamus"}, 1)
        };
        hardQues = new Ques[]{
                new HardQues("Programming language statically typed?", new String[]{"Java", "Python", "JavaScript", "Ruby"}, 0),
                new HardQues("CSS stands for?", new String[]{"Cascading Style Sheets", "Computer Style Sheets", "Colorful Style Sheets", "Creative Style Sheets"}, 0)
        };
    }
    private void start(Ques[] selectedQues) {
        Scanner scanner = new Scanner(System.in);
        for (Ques ques : selectedQues) {
            ques.display();
            System.out.print("Enter your option (1-"+ques.getOptions().length + "):");
            int userAns = scanner.nextInt();
            if (ques.check(userAns - 1)) {
                System.out.println("Correct!\n");
                score++;
            } else {
                System.out.println("Incorrect. Correct answer: "+ques.getCorrect()+"\n");
            }
        }
        System.out.println("Quiz complete! Your score: "+score+"/"+selectedQues.length);
    }
    public void start(String difficulty) {
        Ques[] selectedQues;
        switch (difficulty.toLowerCase()) {
            case "easy":
                selectedQues=easyQues;
                break;
            case "medium":
                selectedQues=mediumQues;
                break;
            case "hard":
                selectedQues=hardQues;
                break;
            default:
                System.out.println("Invalid difficulty level.");
                return;
        }
        shuffle(selectedQues);
        start(selectedQues);
    }
    private void shuffle(Ques[] array) {
        for (int i=array.length-1;i>0;i--) {
            int index=(int)(Math.random()*(i+1));
            Ques temp=array[index];
            array[index]=array[i];
            array[i]=temp;
        }
    }
}
