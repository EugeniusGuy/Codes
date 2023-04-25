# Codes
#header

	#include <stdio.h>
	#define h 3 
	#define w 3 


#main_file

	#include "file6.h"

	int main(void)
	{
	int array[h][w]; 
	float aver; 
	int i;
	int j;
	float sort_ar[h][w+1];
	float buffer[h][w];
	float min_aver = 10000;
	float max_aver = -10000;
	int flag = 1;

	printf("Type numbers of matrix between -10000 and 10000: ");
	for( i = 0; i < h; i++ )
 		for( j = 0; j < w; j++ )
		{
 			scanf("%d", &array[i][j]);
			if ((array[i][j] >= 10000) || (array[i][j] <= -10000))
			{
 				printf("some elements in array are out of terms");
				return 0;
			}
		}

	aver = 0;
	for(i = 0; i < h; i++)
	{
 		for(j = 0; j < w; j++)
		{
 			aver = aver + array[i][j];
			sort_ar[i][j + 1] = array[i][j];
		} 
		aver = aver/w;
		sort_ar[i][0] = aver;
		aver = 0;
	}

	for (i = 0; i < h; i++)
	{
		for (j = 0; j < 1; j++)
		{
			if (sort_ar[i][j] < min_aver)
				min_aver = sort_ar[i][j];
			if (sort_ar[i][j] > max_aver)
				max_aver = sort_ar[i][j];
		}
	}

	while (flag == 1)
	{
		for(i = 0; i < h; i++)
		{
			if(sort_ar[i][0] < sort_ar[i+1][0])
			{
 				for(j = 0; j <= w; j++)
				{
					buffer[i][j] = sort_ar[i][j];
					sort_ar[i][j] = sort_ar[i+1][j];
					sort_ar[i+1][j] = buffer[i][j];
				}
			}
		}
		if((sort_ar[h - 1][0] == min_aver) && (sort_ar[0][0] == max_aver))
		{
			flag = 0;
		}
	}

	for( i = 0; i < h; i++ )
 	{
 		for( j = 0; j <= w; j++ )
		{
 			printf("%4f ", sort_ar[i][j]);
		}
 		printf("\n");
 	}
	return 0;
	}
