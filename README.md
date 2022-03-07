# Regular Expressions

These **ungraded** exercises were designed for you to practice working with Git and Github.

Please read the instructions for each exercise carefully.

**Solve exercises 1 to 6 using Git's command line interface.**

## Exercise 1

1. Clone this repository into your computer.
    * Hint: Use the `git clone` command
1. Open your IDE of choice and add a Java project to this repository as shown below:
    ```
    ├── src
    │   ├── Dog.java
    │   ├── Main.java
    ```
    ```java
    public class Dog {
      String name;
      String breed;
      double height;
      double weight;

      public Dog(String name, String breed, double height, double weight) {
        this.name = name;
        this.breed = breed;
        this.height = height;
        this.weight = weight;
      }

      @Override
      public String toString() {
        return "Hi, my name is " + name + "! " +
                "I'm a " + height + " cm tall " + breed +
                " that weighs " + weight + "kg.";
      }
    }
    ```
    ```java
    public class Main {
      public static void main(String[] args) {
        Dog snuffles = new Dog("Snuffles", "Maltese", 20, 5.5);
        System.out.println(snuffles);

        Dog marley = new Dog("Marley", "Labrador", 55, 29);
        System.out.println(marley);
      }
    }
    ```
1. Using your IDE, compile and run this code.
1. Commit these new files into your local git repository. Do not commit any compiled classes and IDE files!
    - Hint 1: Use the `git add` and `git commit` commands.
    - Hint 2: If you stage files by mistake, use `git reset` to unstage them.
    - Hint 3: Follow the guidelines described [here](https://cbea.ms/git-commit/) when writing your commit messages.
1. Push your changes into your remote git repository. 
    - Hint: Use the `git push` command.
 
## Exercise 3

1. On the `main` branch, create a branch named `new-dogs` from `main` in your local git repository.
    - Hint: Use the `git branch` command.
1. Checkout the `new-dogs` branch.
    - Hint: Use the `git checkout` command.
1. Edit `Main.java` and make it print 3 new dogs.
1. Commit those changes into your local git.
1. Publish the `new-dogs` branch on your remote git repository.
    - Hint: Use the `--set-upstream` option of the `git push` command.
1. Open your https://github.com and verify that your branch has been published there.
1. Merge `new-dogs` into `main`.
    - Hint: Use the `git merge` command.
1. Delete `new-dogs` on your local repository.
    - Hint 1: Use the `--delete` option of the `git branch` command.
    - Hint 2: Use `git branch` to list your local branches.
1. Delete `new-dogs` on your remote repository.
    - Hint 1: Use the `--delete` option of the `git push` command.
    - Hint 2: Use `git branch --all` to list your branches on both your local and your remote repository.
1. Open https://github.com again and verify that your branch was deleted there.

## Exercise 4

1. On the `main` branch, create a `.gitignore` file that ignores:
    * any `.class` file (e.g. `Dog.class`, `Main.class`)
    * any file or directory your IDE may have created
    * any OS-specific file (e.g. `.DS_Store` on macOS)
1. Commit your changes.
1. Push your changes to your remote repository.

## Exercise 5

1. From the `main` branch, create a branch named `owners`.
1. Checkout the `owners` branch.
1. Add `Owner.java` to your application:  
    ```java
    import java.util.ArrayList;
    import java.util.List;

    public class Owner {
      String name;
      List<Dog> dogs;

      public Owner(String name) {
        this.name = name;
        dogs = new ArrayList<>();
      }

      @Override
      public String toString() {
        List<String> dogNames = new ArrayList<>();

        for (Dog dog : dogs)
          dogNames.add(dog.name);

        String dogList = "[" + String.join(", ", dogNames) + "]";

        return "Hi, I'm " + name + "! I own these dogs: " + dogList;
      }
    }
    ```
1. Modify `Main.java` as shown below:
    ```java
    public class Main {
      public static void main(String[] args) {
        Owner morty = new Owner("Morty");

        Dog snuffles = new Dog("Snuffles", "Maltese", 20, 5.5);
        morty.dogs.add(snuffles);
        System.out.println(snuffles);

        Dog marley = new Dog("Marley", "Labrador", 55, 29);
        morty.dogs.add(marley);
        System.out.println(marley);

        System.out.println(morty);
      }
    }
    ```
1. Commit your changes to your local repository.
1. Push your changes to your remote repository.
1. Checkout the `main` branch.
1. Edit `Dog.java` as shown below:
    ```java
    public class Dog {
      String name;
      String breed;
      double height;
      double weight;
      int age;

      public Dog(String name, String breed, double height, double weight, int age) {
        this.name = name;
        this.breed = breed;
        this.height = height;
        this.weight = weight;
        this.age = age;
      }

      @Override
      public String toString() {
        return "Hi, my name is " + name + "! " +
                "I'm a " + height + " cm tall " + breed +
                " that weighs " + weight + "kg. " +
                "I'm " + age + " years old.";
      }
    }
    ```
1. Edit `Main.java` to fix the invocation of `new Dog()` (i.e. add the `age` parameter when creating `Dog` objects)
1. Add and commit your changes to your local repository.
1. Push your changes to your remote repository.
1. Merge `owners` into `main`.
1. Resolve the conflicts git will identify. In the resulting code, your `Dog` class must have the age attribute (including in its constructor) and the `Owner` object must be created and printed on the `main()`.
1. Create a merge commit.
1. Push the merge to your remote repository.

## Exercise 6

1. On the `main` branch, add a `Cat.java` file:
    ```java
    public class Cat {
      String name;
      String favoriteFood;

      public Cat(String name, String favoriteFood) {
        this.name = name;
        this.favoriteFood = favoriteFood;
      }

      @Override
      public String toString() {
        return name + ": I'm a cat and I love to eat " + favoriteFood;
      }
    }
    ```
1. Add and commit this change to your local repository.
1. Reverse this last commit in a way that it is removed from your repository's history.
    - Hint 1: Use the `git reset` command.
    - Hint 2: To see your repository's history, use the `git log` command.
1. Commit `Cat.java` again.
1. Reverse this last commit in a way that it remains in from your repository's history.
    - Hint: Use the `git revert` command.
1. Push these changes to your remote repository.

## Exercise 7

1. On your local repository, delete all branches besides `main`.
1. On your remote repository, delete all branches besides `main`.
1. Close your IDE.
1. Delete the directory containing your local git repository.
1. Download a Git client with a graphical user interface (e.g. Github Desktop, Git Kraken).
1. Redo exercises 1 to 6 using the client you just downloaded.

## Resources 

* [A short video explaining what GitHub is](https://www.youtube.com/watch?v=w3jLJU7DT5E&feature=youtu.be) 
* [Git and GitHub learning resources](https://docs.github.com/en/github/getting-started-with-github/git-and-github-learning-resources) 
* [Understanding the GitHub flow](https://guides.github.com/introduction/flow/)
* [How to use GitHub branches](https://www.youtube.com/watch?v=H5GJfcp3p4Q&feature=youtu.be)
* [Interactive Git training materials](https://githubtraining.github.io/training-manual/#/01_getting_ready_for_class)
* [GitHub's Learning Lab](https://lab.github.com/)
