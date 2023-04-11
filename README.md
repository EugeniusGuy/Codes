# Codes
#header

	#include <stdio.h>
	#define len 10


#main_file

	#include "file5.h"

	int main(void)
	{
	int seq[len];  
	int elem;
	int count = 0;
	
	printf("Type 10 numbers between -10000 and 10000: ");
	
	for(elem = 0; elem < len; elem++)
	{
		scanf("%d", &seq[elem]);
		if ((seq[elem] >= 10000) || (seq[elem] <= -10000))
		{
 			printf("some elements in array are out of terms");
			return 0;
		}
	}
	for(elem = 0; elem < len; elem++)
 	{
 		if(seq[elem] == (seq[elem-1] + seq[elem+1])/2)
		{
			count = count + 1;
		}
 	}

	if (count > 0)
	{
		if(count == len - 2)
		{
			printf("All elements are arythmethic progression");
		}
		else
		{
			printf("Some elements are arythmethic progression");
		}
	}
	else
	{
		printf("Elements are'nt arythmethic progression");
	}
	return 0;
	}
