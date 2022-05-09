# Lab Report 3 Week 6

## **Streamlining ssh Configuration**
---
### **My config file was created and edited using VSCode:**
![config](lr3_ss\Screenshot_1.png)

### **Logging in using the alias:**
![logging in](lr3_ss\Screenshot_2.png)

### **Using scp command with alias**
![scp command](lr3_ss\Screenshot_3.png)
ls command in ieng6

![ls command in ieng6](lr3_ss\Screenshot_4.png)

---
## **Setup Github Access from ieng6(unsuccessful)**

I could not properly setup the github key. I made a new ssh key called "github" and "github.pub". I copied it over to the .ssh folder in ieng6, but was unsuccsessful in adding it to the ssh-agent. Here are screenshots:

### 1.Showing location in ieng6 and trying to add to ssh-agent:
![key loc and command](lr3_ss\Screenshot_5.png)

---

## **Copy whole directories with scp -r**

### **Copying markdown parse into ieng6 using scp -r**
![scp -r terminal1](lr3_ss\Screenshot_6.png)
![scp -r terminal2](lr3_ss\Screenshot_7.png)

### **Logging into ieng6 and running test**
![login and test](lr3_ss\Screenshot_8.png)

### **Running all commands in one line(unsuccessful)**
I could not get the commands once logged into ieng6 to run. Markdown-parser would be copied and it logs into ieng6 but when trying to compile and run the test I get errors. But the files do run and the tests pass if I run each command one by one normally, as seen in the previous step.
![error1](lr3_ss\Screenshot_9.png)
![error2](lr3_ss\Screenshot_10.png)
![error3](lr3_ss\Screenshot_11.png)
![error4](lr3_ss\Screenshot_12.png)
![error5](lr3_ss\Screenshot_13.png)

