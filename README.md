# Codes
#header

	#include <stdio.h>
	#define YES 1
	#define NO 0
	#define MAXLINE 1000

	void process_line(char buffer[]);
	int break_flag = 0;


#main_file

	#include "file4.h"

	int main(void)

 	{	
 
	char line[MAXLINE];
	printf("Type text: ");
	gets(line);
	process_line(line);
	if(break_flag == 1)
	{
		printf("You've typed something except letters \n");
		return 0;
	}
	else
		printf("Fixed text: %s\n", line);
	return 0;

        }
	void process_line(char buffer[])


	{

	char sym; 
	int count = 0;
	int length;
	int flag; 
	int found; 
	int i; 
	int pos; 
	int start; 
	int j;
	
	flag = NO;
	found = NO;
	start = 0;
 	i = 0;
	pos = 0;
	printf("Type length of the word: ");
	scanf("%d", &length);

	do
	{
		sym = buffer[i];
		if ((sym >= 'a' && sym <= 'z') || (sym >= 'A' && sym <= 'Z') || sym == ' ' || sym == '.' || sym == ',' || sym == '\n' || sym == '\0' || sym == ';' || sym == '!' || sym == '?' || sym == ':' || sym == '-')
		{
 		if(sym == ' ' || sym == '.' || sym == ',' || sym == '\n' || sym == '\0' || sym == ';' || sym == '!' || sym == '?' || sym == ':' || sym == '-')
 		{
 			if(flag == YES)
 			{
				if(found == NO)
				{
 					for(j = start; j < i; j++)
 						buffer[pos++] = buffer[j];
 				}
 			}
 			flag = NO;
			count = 0;
 			buffer[pos++] = sym;
 		}
 		else
 		{
			count = count + 1;
 			if(flag == NO)
			{
 				start = i; 
			}
 			if( count > length )
			{
 				found = YES;
			}
 			else
			{
 				found = NO;
			}
 			flag = YES;
 		}
 		i++;
		}
		else
		{
			break_flag = 1;
			break;
		}
	}
	while((sym != '\0') & (break_flag != 1));
} 
