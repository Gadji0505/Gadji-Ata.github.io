import java.util.*;
class Student {
private String fio,adress, fakulty;
private int kurs;
private int []marks;

Student(String fio,String adress,String fakulty,
int kurs,int []marks)
{
 this.fio=fio;
 this.adress=adress;
 this.fakulty=fakulty;
 this.kurs=kurs;
 this.marks=marks;
}
String getFio(){return fio;}

void setFio(String fio){this.fio=fio;}

double sr(){
double s=0;
for (int i=0;i<marks.length;i++)
    s+=marks[i];
return s/marks.length;
}
/*void print(){
String s=" ";
for (int i=0;i<marks.length;i++)
 { s+=marks[i];
    s+=" ";}
    System.out.println("Студент "+this.fio+"\n Адрес "+adress+"\n Факультет "+fakulty+"\n Курс "+kurs+"\n Оценки "+s);
}*/

public String toString(){
String s=" ";
for (int i=0;i<marks.length;i++)
 { s+=String.valueOf(marks[i]);
    s+=" ";}
return "Студент "+fio+"\n Адрес "+adress+"\n Факультет "+fakulty+"\n Курс "+kurs+"\n Оценки "+s+"\n ";
}
}
class StudentGroup{
ArrayList <Student> a;
StudentGroup()
{a=new ArrayList<Student>();}

void add(Student s){
a.add(s);
}
void del(String fio)
{
int p=-1;
for (int i=0;i<a.size();i++)
    if (fio.equalsIgnoreCase(a.get(i).getFio())) p=i;
if (p>-1) {
a.remove(p);
    System.out.println("Удалили студента "+fio);
}
else  System.out.println("Такого студента нет");
}
void print(){
for (int i=0;i<a.size();i++)
  System.out.println(a.get(i).toString());
}
}
Метод сортировки (пузырёк) в алфавитном порядке(реверс), курсу, выборка по фамилии/факультету/курсу


public class StudentProject {

    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
      Scanner sc=new Scanner(System.in);
        StudentGroup sg=new StudentGroup();
      System.out.println("Введите ко-во студентов");
      int n=sc.nextInt();
      String q=sc.nextLine();
      for (int j=0;j<n;j++){
      System.out.println("Введите фамилию");
      String f=sc.nextLine();
      System.out.println("Введите адрес");
      String ad=sc.nextLine();
      System.out.println("Введите факультет");
      String fak=sc.nextLine();
      System.out.println("Введите курс");
      int kurs=sc.nextInt();
      System.out.println("Введите ко-во оценок");
      int k=sc.nextInt();
      int []m=new int[k];
      System.out.println("Введите оценки");
      for (int i=0;i<k;i++)
        m[i]=sc.nextInt();
      Student st=new Student(f,ad,fak,kurs,m);
      sg.add(st);
      q=sc.nextLine();
        }
      System.out.println("Кого удалить из списка?");
     String f=sc.nextLine();
     sg.del(f);
     sg.print();
    }
    
}
