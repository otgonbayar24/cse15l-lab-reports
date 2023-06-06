What environment are you using (computer, operating system, web browser, terminal/editor, and so on)?

The user is using a MacOS operating system, iTerm2 terminal, IntelliJ IDEA IDE for Java programming, and Vim for editing bash scripts.

Detail the symptom you're seeing. Be specific; include both what you're seeing and what you expected to see instead. Screenshots are great, copy-pasted terminal output is also great. Avoid saying “it doesn't work”.

When the user runs the Java program using a bash script, they get an output "The file does not exist :(". However, they expect the output to be "File exists, yay!" as the file they are trying to access does indeed exist in the directory.

Detail the failure-inducing input and context. That might mean any or all of the command you're running, a test case, command-line arguments, working directory, even the last few commands you ran. Do your best to provide as much context as you can.

The user runs a bash script named "run.sh" that is supposed to compile and execute the Java program. The Java program is supposed to check if a file named "test.txt" exists.

![Screenshot 2023-06-05 212240.png](https://github.com/otgonbayar24/cse15l-lab-reports/blob/main/Screenshot%202023-06-05%20212240.png)
![Screenshot 2023-06-05 212231.png](https://github.com/otgonbayar24/cse15l-lab-reports/blob/main/Screenshot%202023-06-05%20212231.png)
![Screenshot 2023-06-05 213825.png](https://github.com/otgonbayar24/cse15l-lab-reports/blob/main/Screenshot%202023-06-05%20213825.png)
![Screenshot 2023-06-05 213830.png](https://github.com/otgonbayar24/cse15l-lab-reports/blob/main/Screenshot%202023-06-05%20212231.png)



Ta's response:
Have you checked the working directory when the Java program is running? Try printing out the absolute path of the file in your Java program and see where it's looking for the file.

Follow-up:

Added the following line of code in the Java program to print the absolute path of the file:
![Screenshot 2023-06-05 214311.png](https://github.com/otgonbayar24/cse15l-lab-reports/blob/main/Screenshot%202023-06-05%20214311.png)

After running the "run.sh" script again, got this output:
![Screenshot 2023-06-05 214316.png](https://github.com/otgonbayar24/cse15l-lab-reports/blob/main/Screenshot%202023-06-05%20214316.png)
Bug:

The bug is due to the fact that the user first navigates into the src directory in the bash script and then tries to run the Java program. When the program runs, its working directory is src, and it's looking for the test.txt file in the src directory, but the test.txt file is in the root directory of the project.

Bug Fixing Information:
To fix the bug, edit the "run.sh" bash script to first compile the Java program in the src directory and then move back to the root directory before executing the Java program:
![Screenshot 2023-06-05 215258.png](https://github.com/otgonbayar24/cse15l-lab-reports/blob/main/Screenshot%202023-06-05%20215258.png)
![Screenshot 2023-06-05 215317.png](https://github.com/otgonbayar24/cse15l-lab-reports/blob/main/Screenshot%202023-06-05%20215317.png)
![Screenshot 2023-06-05 215321.png](https://github.com/otgonbayar24/cse15l-lab-reports/blob/main/Screenshot%202023-06-05%20215321.png)
![Screenshot 2023-06-05 215325.png](https://github.com/otgonbayar24/cse15l-lab-reports/blob/main/Screenshot%202023-06-05%20215325.png)

This way, the input argument will be correctly passed to the Java program, and it should print the square of the input as expected.Here, /path/to/root_project_directory should be replaced by the actual path to the project's root directory. As you can see, the file path is now correct, and the Java program correctly reports that the file exists.



Reflection


 For the second half, my familiarity with backend processes and handling URL requests has improved significantly. The ability to work with web servers, which seemed challenging before this quarter, is now within my comfort zone.
Working hands-on with the terminal has also been a fundamental part of my learning process. I have not only learned about web servers and their operations, but also developed a systematic approach to debugging code.
A deeper understanding of terminal commands such as cat, less, grep, along with their various options, has also been an integral part of my learning. I am confident that these skills will play a pivotal role in my future programming endeavors.
Also, the course has enabled me to work effectively with vim and bash scripts, enhancing my versatility in coding and debugging
