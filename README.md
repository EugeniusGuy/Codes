# Codes
#header

	#include <stdio.h>
	#define N 3 
	#define K 3 


#main_file

	int main(void)
	{
	int array[N][K]; 
	float aver; 
	int i;
	int j;
	float sort_ar[N][K+1];
	float buffer[N][K];
	float min_aver = 10000;
	float max_aver = -10000;
	int flag = 1;

	printf("Type numbers of matrix between -10000 and 10000:\n ");
	for( i = 0; i < N; i++ )
 		for( j = 0; j < K; j++ )
		{
 			scanf("%d", &array[i][j]);
			if ((array[i][j] >= 10000) || (array[i][j] <= -10000))
			{
 				printf("some elements in array are out of terms");
				return 0;
			}
		}

	aver = 0;
	for(i = 0; i < N; i++)
	{
 		for(j = 0; j < K; j++)
		{
 			aver = aver + array[i][j];
			sort_ar[i][j + 1] = array[i][j];
		} 
		aver = aver/K;
		sort_ar[i][0] = aver;
		aver = 0;
	}

	for (i = 0; i < N; i++)
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
		for(i = 0; i < N; i++)
		{
			if(sort_ar[i][0] < sort_ar[i+1][0])
			{
 				for(j = 0; j <= K; j++)
				{
					buffer[i][j] = sort_ar[i][j];
					sort_ar[i][j] = sort_ar[i+1][j];
					sort_ar[i+1][j] = buffer[i][j];
				}
			}
		}
		if((sort_ar[N - 1][0] == min_aver) && (sort_ar[0][0] == max_aver))
		{
			flag = 0;
		}
	}

	for( i = 0; i < N; i++ )
 	{
 		for( j = 1; j <= K; j++ )
		{
 			printf("%4f ", sort_ar[i][j]);
		}
 		printf("\n");
 	}
	return 0;
	}

#Header 7

	#include <stdio.h>
#main_file 7

	int main(void)
	{
  	long N;
  	unsigned long calc_num;
  	int mask = 1;
  	int scan_check; 

  	printf("Enter a number: ");
  	scan_check = scanf("%ld", &N); 

  	if (scan_check != 1) 
  	{
    		printf("Wrong input\n");
    		return 0;
  	}

  	calc_num = (unsigned long)N;

  	while( calc_num % 2 != 1 ) 
   	{
     		mask = mask * 2;
     		calc_num >>= 1;
   	}

  	printf("Result: %d\n", mask);
  	return 0;
	}
