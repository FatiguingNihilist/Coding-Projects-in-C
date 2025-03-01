#Programming/c/database

**_`NOTE`:This is Purely a documentation of learning databases and by no means is this a tutorial or guide to make a database. I just want to document my journey. So you can't blame if some of the Code is God awful. Also sometimes i give long ass explanations so just read the TL;DR if you don't want to read it all._** 
## Introduction
So I have recently gotten that itch to make something It truly is something I cannot control so, I decided to make a Data-Base in C (as it is my favorite programming language).

## Initial Questions
I have used some Sqlite3 before but it really is just a black box to me. I hope that this gives me a better understanding of database. The Questions I have are:

1. How are databases files formatted and made?
2. How are they managed?
3. How can we make Tables and retrieve data form them?

### Repl (1st March)
So sqlite first runs a repl (Read-Evalute-Process-Loop) So we can implement that in C using following Code:

Header file:
```C
#include <stdio.h>
#include <string.h>
#include <stdlib.h>
```

`stdio.h`: This a C standard library and it is used for Input and Output and it's full form is "Standard Input and Output". It has some basic Functions like `printf`,`scanf` and `fprintf` etc.

`string.h`: This is a library for strings aka char \*s' It has functions like `strlen` and `strcmp` etc.

`stdlib.h`: This is a library used for a Lot of different cases for example `exit` and others. 

Main-Function:
```C
int main(void)
{
	char input[MAX_LENGTH];
	char command[MAX_LENGTH/2], argument[MAX_LENGTH/2]; 
	while(1){
	repl(input, command, argument);
	}
	return 0;
}
```

In this function we are calling the repl function which we make ourselves. If your wondering why I am making the variables for input, command and argument in the main function why not just in the repl function the reason is _"yes"_. `MAX_LENGTH` is a macro I defined you can let this equal to whatever length you want your string to be.

Repl-function:
```C
void repl(char input[], char command[], char argument[])
{
	printf(">");
	fgets(input, MAX_LENGTH, stdin);
	input[strlen(input)] == '\0'
	sscanf(input, "%[a-zA-Z] %[a-zA-Z.,]", command, argument);
}
```

The Repl function just gets input from user and breaks it into an argument and command. It consists of the following parts:

`printf`: Just to show the user the basic prompt.
`fgets`: It is used to get input from user.

_**`NOTE: Never use gets and scanf for string input because scanf will just not work with input that has whitespace characters in it Translation--> It can't handle spaces and for gets it is just unsasfe Learn More at [here](https://www.google.com/url?sa=t&source=web&rct=j&opi=89978449&url=https://www.geeksforgeeks.org/gets-is-risky-to-use/&ved=2ahUKEwjh4J3onumLAxVQcfUHHUldAGUQFnoECBQQAw&usg=AOvVaw0MTYxCksHETACxjriQIkEr)`**_

`input[strlen(input)] == '\0'`: This will just make it so that the trailing newline that fgets leaves is removed. To Explain further fgets leaves a newline at the end of every string for example if the user enters: "Hello" fgets will attach a '\n' at the end of the end of the string so it becomes "Hello\n". The reason I don't like this is because functions like `scanf` will just take the \n as input not the user input for example in the following code:
```C
int main(void)
	char *string;
	int c;
	fgets(string, 100, stdin);
	scanf("%d", &c);
	return 0;
}
```
You will see that the program will just end without asking the user to enter any input at the `scanf`. so I just like to remove it and write a '\0' at it's place. so we access the last index of the string and replace the \n with a \0.

TL;DR: It removes the \n at the end of the string.

`sscanf`: This is used for parsing input. it has the following syntax:

sscanf(input, "format-specifiers", variables_set_to_recieve_parsed_input);

What sscnaf does is that it takes a string which you want to parse and then we set the format specifiers and since there are no specific format specifiers which are used for inputting characters a-z and nothing else so we just this syntax:

"%[a-zA-Z]"

What is this you ask? well it is a character set so we are just making the sscanf function accept all the letters of the alphabet from a-z and also capital A-Z.

TL;DR: It simply takes a string and separates it to different variables depending upon format specifiers.

## Commands
Finally after all load shit you just read(hopefully ;D). So now we can get ready to implement some commands for making database files and editing them.

### Making db files
So full disclaimer the "db" files will just be .txt files. so for that purpose we can set it up so that if the user enters in the prompt that "makedb name" then we will make a file with that name.

makedb-function:
```C
makedb(char file name[])
{
	
}
```