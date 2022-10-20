# Safe-Case-System
import java.io.File;
import java.io.FileNotFoundException;
import java.io.IOException;
import java.util.Arrays;
import java.util.Collections;
import java.util.List;
import java.util.Scanner;

public class VirtRep {
    public static void main(String[] args) throws FileNotFoundException {
        Scanner user = new Scanner(System.in);
        int x;
        File dir = new File("C:\\Users\\hp\\Desktop\\Simplilearn");

        //  Display();

        System.out.println("Welcome to  Safe Case System");
        System.out.println("1- Product and Owner Description  \n 2- Go to the Application");
        int z = user.nextInt();
        if (z == 1) {
            System.out.println("Welcome to  Safe Case System");
            System.out.println("This Product Is All About File Handling And Managing It\n\n There are several operation in this application like Displaying the files in Directory , Adding New files , Deleting , Searching e.t.c\n\nProduct Owner Rishabh Yadav\n\n E-mail : rishabhyadavalld97@gmail.com");
        } else if (z == 2) {
          EnterApp();
        }
    }

    // Enter inside App
    public static void EnterApp(){

        System.out.println(" 1- Display all file in Directory \n 2-Operations on File \n 3- Close the Application");
        System.out.println("Choose from the above options");
        Scanner opt= new Scanner(System.in);
        int x = opt.nextInt();

        if (x == 1) {
            // to display all the files in the directory
            Display();
        }
        else if (x == 2) {
            // Shows option for the User
            UserInterface();
        }

        else if (x == 3) {
            // Closes the Program
            System.out.println("Your application is close now");
            System.exit(0);
        }
        else {
            System.out.println(" Invalid Selection Choose between 1-3");
            EnterApp();
        }

    }


    // Display The Files
    public static void Display(){
    File dir = new File("C:\\Users\\hp\\Desktop\\Simplilearn");
    String contents[] = dir.list();
            System.out.println("List of unsorted files  in the specified directory:");
            for(
    int i = 0;
    i<contents.length;i++)

    {
        System.out.println(contents[i]);
    }

    List listFile = null;
            if(dir.isDirectory())

    {
        listFile = Arrays.asList(dir.list());
    }
            Collections.sort(listFile);
            System.out.println("Sorting by filename in ascending order");
            System.out.println("--------------------------------");
            for(
    Object s :listFile)

    {
        System.out.println(s);
    }
            System.out.println("--------------------------------");
}
public static void UserInterface()
    {
        //Welcome to User Interface

        System.out.println("1- Add new file to dir\n 2-Delete file\n 3 - Search file\n 4- Back to home ");
        System.out.println("Choose from the above options");
        Scanner cus= new Scanner(System.in);
        int y = cus.nextInt();

        if (y == 1) {
            AddFile();
        }
        else if (y == 2) {
            DeleteFile();
        }
        else if (y == 3) {
            SearchFile();
        }
        else if (y == 4) {
          UserInterface();
        }
        else {
            System.out.println("Invalid Choice");
            UserInterface();
        }

    }

// Add the Files
        public static void AddFile() {
        try {
            System.out.println("Enter the file name");
            Scanner sc = new Scanner(System.in);
            String inputFileName = sc.nextLine();
            File input = new File(inputFileName);
            if (input.createNewFile()) {
                System.out.println("File created: " + input.getName());

            } else {
                System.out.println("File already exists.");
            }
        } catch (IOException e) {
            System.out.println("An error has occurred.");
            e.printStackTrace();
        }
    }

    // Deletion of file
    public static void DeleteFile() {
        System.out.println("Enter the file you want to delete from directory");
        Scanner del = new Scanner(System.in);
        String deleteFileName = del.nextLine();
        File deleteFile = new File(deleteFileName);

        //deletion of file
        if (deleteFile.exists()) {
            if (deleteFile.delete()) {
                System.out.println(deleteFileName + "File got deleted");
            }
        } else {
            System.out.println("No such file exist");
        }

    }
    //Search the files
     public static void SearchFile() {
        //Searching the file


        Scanner search = new Scanner(System.in);
        System.out.println("Enter the name of file you want to search");
        String file = search.nextLine();
        File sch = new File("C:\\Users\\hp\\Desktop\\Simplilearn");
        String arr[] = sch.list();

        int a = 0;
        if (arr == null) {
            System.out.println("Empty directory.");
        } else {
            for (int i = 0; i < arr.length; i++) {
                String fileName = arr[i];
                if (fileName.equalsIgnoreCase(file)) {
                    System.out.println("File found" + "  " + file);
                    a++;
                }
            }
        }
        if (a == 0) {
            System.out.println("File not found");
        }

    }
}
