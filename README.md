# Codes
#header

	#include <stdio.h>
	#define YES 1
	#define NO 0
	#define MAXLINE 1000

	int break_flag = 0;


#main_file
	
	#include "file8.h"

	void process_line(char buffer[]);

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
	int length; 
	int flag; 
	int found;
	char *in_ptr; 
	char *out_ptr; 
	char *word_ptr;
	int count = 0; 

	flag = NO;
	found = NO;
	word_ptr = buffer;
	in_ptr = buffer;
	out_ptr = buffer;
	printf("Type length of the word: ");
	scanf("%d", &length);

	do
 	{
 		sym = *in_ptr;
		if ((sym >= 'a' && sym <= 'z') || (sym >= 'A' && sym <= 'Z') || sym == ' ' || sym == '.' || sym == ',' || sym == '\n' || sym == '\0' || sym == ';' || sym == '!' || sym == '?' || sym == ':' || sym == '-')
		{ 
 		if(sym == ' ' || sym == '.' || sym == ',' || sym == '\n' || sym == '\0' || sym == ';' || sym == '!' || sym == '?' || sym == ':' || sym == '-')
 		{
 			if( flag == YES )
 			{
 				if( found == NO )
 				{
 					while( word_ptr < in_ptr )
 						*out_ptr++ = *word_ptr++;
 				}
 			}
 			flag = NO;
			count = 0;
 			*out_ptr++ = sym;
 		}
 		else
 		{
			count = count + 1;
 			if( flag == NO )
 				word_ptr = in_ptr; 
 			if( count > length )
 				found = YES;
 			else
 				found = NO;

 			flag = YES;
 		}

 		in_ptr++;
		}
		else
		{
			break_flag = 1;
			break;
		} 
 	}
	while(sym != '\0');
	}
