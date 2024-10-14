Student.java — класс студента:
java
Копировать код
import java.util.*;

class Student {
    private String fio, adress, fakulty;
    private int kurs;
    private int[] marks;

    Student(String fio, String adress, String fakulty, int kurs, int[] marks) {
        this.fio = fio;
        this.adress = adress;
        this.fakulty = fakulty;
        this.kurs = kurs;
        this.marks = marks;
    }

    String getFio() {
        return fio;
    }

    void setFio(String fio) {
        this.fio = fio;
    }

    double sr() {
        double s = 0;
        for (int i = 0; i < marks.length; i++) {
            s += marks[i];
        }
        return s / marks.length;
    }

    @Override
    public String toString() {
        String s = " ";
        for (int i = 0; i < marks.length; i++) {
            s += String.valueOf(marks[i]);
            s += " ";
        }
        return "Студент " + fio + "\n Адрес " + adress + "\n Факультет " + fakulty + "\n Курс " + kurs + "\n Оценки " + s + "\n ";
    }
}

StudentGroup.java — класс группы студентов:
java
Копировать код
import java.util.*;

class StudentGroup {
    ArrayList<Student> a;

    StudentGroup() {
        a = new ArrayList<Student>();
    }

    void add(Student s) {
        a.add(s);
    }

    void del(String fio) {
        int p = -1;
        for (int i = 0; i < a.size(); i++) {
            if (fio.equalsIgnoreCase(a.get(i).getFio())) p = i;
        }
        if (p > -1) {
            a.remove(p);
            System.out.println("Удалили студента " + fio);
        } else {
            System.out.println("Такого студента нет");
        }
    }

    void print() {
        for (int i = 0; i < a.size(); i++) {
            System.out.println(a.get(i).toString());
        }
    }
}
StudentProject.java — основной класс для работы с пользователем:
java
Копировать код
import java.util.*;

public class StudentProject {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        StudentGroup sg = new StudentGroup();

        System.out.println("Введите ко-во студентов");
        int n = sc.nextInt();
        String q = sc.nextLine();  // для обработки перехода на новую строку

        for (int j = 0; j < n; j++) {
            System.out.println("Введите фамилию");
            String f = sc.nextLine();
            System.out.println("Введите адрес");
            String ad = sc.nextLine();
            System.out.println("Введите факультет");
            String fak = sc.nextLine();
            System.out.println("Введите курс");
            int kurs = sc.nextInt();
            System.out.println("Введите ко-во оценок");
            int k = sc.nextInt();
            int[] m = new int[k];
            System.out.println("Введите оценки");
            for (int i = 0; i < k; i++) {
                m[i] = sc.nextInt();
            }
            Student st = new Student(f, ad, fak, kurs, m);
            sg.add(st);
            q = sc.nextLine();  // для обработки перехода на новую строку
        }

        System.out.println("Кого удалить из списка?");
        String f = sc.nextLine();
        sg.del(f);
        sg.print();
    }
}
Теперь ты можешь скопировать и вставить каждый класс в отдельный файл, сохранив их с именами Student.java, StudentGroup.java и StudentProject.java.