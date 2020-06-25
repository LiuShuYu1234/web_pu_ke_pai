#include<stdio.h>
#define T 10
#define J 11
#define Q 12
#define K 13
#define A 14
struct pai
{
	int num;
	char color;
};

int santiao[2],st=0,liangdui[2][2],ld=0,ld1=0,max[2],m=0,min[2],n=0,duizi[2],dz=0;

int tong_hua_shun(pai *p)
{
	int i,index=0,index1=0;
	for(i=0;i<4;i++)
	{
		if(p[i].color!=p[i+1].color)
		{
			index++;
		}
	}
	if(index==0)
	{
		for(i=0;i<4;i++)
		{
			if(p[i].num+1!=p[i+1].num)
			{
				index1++;
			}
		}
		if(index1==0)
		{
			return 1;
		}
		else
		{
			return 0;
		}
	}
	else
	{
		return 0;
	}
}

int tong_hua(pai *p)
{
	int i,index=0;
	for(i=0;i<4;i++)
	{
		if(p[i].color!=p[i+1].color)
		{
			index++;
		}
	}
	if(index==0)
	{
		return 1;
	}
	else
	{
		return 0;
	}
}

int shun_zi(pai *p)
{
	int i,index=0;
	for(i=0;i<4;i++)
	{
		if(p[i].num+1!=p[i+1].num)
		{
			index++;
		}
	}
	if(index==0)
	{
		return 1;
	}
	else
	{
		return 0;
	}
}

int san_tiao(pai *p)
{
	int i,j,k,index=0;
	for(i=0;i<5;i++)
	{
		for(j=i+1;j<5;j++)
		{
			for(k=j+1;k<5;k++)
			{
				if(p[i].num==p[j].num&&p[j].num==p[k].num)
				{
					index++;
					santiao[st]=p[i].num;
					st++;
				}
			}
		}
	}
	if(index!=0)
	{
		return 1;
	}
	else
	{
		return 0;
	}
}

int liang_dui(pai *p)
{
	int i,j,index=0;
	for(i=0;i<5;i++)
	{
		for(j=i+1;j<5;j++)
		{
			if(p[i].num==p[j].num)
			{
				index++;
				liangdui[ld][ld1]=p[i].num;
				ld1++;
				continue;
			}
		}
	}
	if(liangdui[ld][0]>liangdui[ld][1])
	{
		max[m]=liangdui[ld][0];
		m++;
		min[n]=liangdui[ld][1];
		n++;
	}
	else
	{
		max[m]=liangdui[ld][1];
		m++;
		min[n]=liangdui[ld][0];
		n++;
	}
	ld++;
	if(index==2)
	{
		return 1;
	}
	else
	{
		return 0;
	}
}

int dui_zi(pai *p)
{
	int i,j,index=0;
	for(i=0;i<5;i++)
	{
		for(j=i+1;j<5;j++)
		{
			if(p[i].num==p[j].num)
			{
				duizi[dz]=p[i].num;
				dz++;
				index++;
			}
		}
	}
	if(index==1)
	{
		return 1;
	}
	else
	{
		return 0;
	}
}

int main()
{
	pai black[5],white[5];
	char number[5];
	int i,a[5],b[5],index;
	printf("Black:");
	scanf("%c%c %c%c %c%c %c%c %c%c",&number[0],&black[0].color,&number[1],&black[1].color,&number[2],&black[2].color,&number[3],&black[3].color,&number[4],&black[4].color);
	for(i=0;i<5;i++)
	{
		if(number[i]=='T')
		{
			black[i].num=10;
		}
		else if(number[i]=='J')
		{
			black[i].num=11;
		}
		else if(number[i]=='Q')
		{
			black[i].num=12;
		}
		else if(number[i]=='K')
		{
			black[i].num=13;
		}
		else if(number[i]=='A')
		{
			black[i].num=14;
		}
		else
		{
			black[i].num=number[i]-'0';
		}
	}
	getchar();
	printf("White:");
	scanf("%c%c %c%c %c%c %c%c %c%c",&number[0],&white[0].color,&number[1],&white[1].color,&number[2],&white[2].color,&number[3],&white[3].color,&number[4],&white[4].color);
	for(i=0;i<5;i++)
	{
		if(number[i]=='T')
		{
			white[i].num=10;
		}
		else if(number[i]=='J')
		{
			white[i].num=11;
		}
		else if(number[i]=='Q')
		{
			white[i].num=12;
		}
		else if(number[i]=='K')
		{
			white[i].num=13;
		}
		else if(number[i]=='A')
		{
			white[i].num=14;
		}
		else
		{
			white[i].num=number[i]-'0';
		}
	}
	for(i=0;i<5;i++)//散牌的规则比较 ,index=1为黑牌大，index=0为白牌大，index=-1为一样大 
	{
		a[i]=black[i].num;
	}
	for(i=0;i<5;i++)
	{
		b[i]=white[i].num;
	}
	if(a[4]>b[4])
	{
		index=1;
	}
	else if(a[4]<b[4])
	{
		index=0;
	}
	else if(a[4]==b[4])
	{
		if(a[3]>b[3])
		{
			index=1;
		}
		else if(a[3]<b[3])
		{
			index=0;
		}
		else
		{
			if(a[2]>b[2])
			{
				index=1;
			}
			else if(a[2]<b[2])
			{
				index=0;
			}
			else
			{
				if(a[1]>b[1])
				{
					index=1;
				}
				else if(a[1]<b[1])
				{
					index=0;
				}
				else
				{
					if(a[0]>b[0])
					{
						index=1;
					}
					else if(a[0]<b[0])
					{
						index=0;
					}
					else
					{
						index=-1;
					}
				}
			}
		}
	}
	if(tong_hua_shun(black)==1&&tong_hua_shun(white)==0)//开始判断牌的大小 
	{
		printf("Black wins");
	}
	else if(tong_hua_shun(black)==0&&tong_hua_shun(white)==1)
	{
		printf("White wins");
	}
	else if(tong_hua_shun(black)==1&&tong_hua_shun(white)==1)
	{
		if(black[4].num>white[4].num)
		{
			printf("Black wins");
		}
		else if(black[4].num<white[4].num)
		{
			printf("White wins");
		}
		else if(black[4].num==white[4].num)
		{
			printf("Tie");
		}
	}
	else if(tong_hua_shun(black)==0&&tong_hua_shun(white)==0)
	{
		if(tong_hua(black)==1&&tong_hua(white)==0)
		{
			printf("Black wins");
		}
		else if(tong_hua(black)==0&&tong_hua(white)==1)
		{
			printf("White wins");
		}
		else if(tong_hua(black)==1&&tong_hua(white)==1)
		{
			if(index==1)
			{
				printf("Black wins");
			}
			else if(index==0)
			{
				printf("White wins");
			}
			else if(index==-1)
			{
				printf("Tie");
			}
		}
		else if(tong_hua(black)==0&&tong_hua(white)==0)
		{
			if(shun_zi(black)==1&&shun_zi(white)==0)
			{
				printf("White wins");
			}
			else if(shun_zi(black)==0&&shun_zi(white)==1)
			{
				printf("White wins");
			}
			else if(shun_zi(black)==1&&shun_zi(white)==1)
			{
				if(a[4]>b[4])
				{
					printf("Black wins");
				}
				else if(a[4]<b[4])
				{
					printf("White wins");
				}
				else if(a[4]==b[4])
				{
					printf("Tile");
				}
			}
			else if(shun_zi(black)==0&&shun_zi(white)==0)
			{
				if(san_tiao(black)==1&&san_tiao(white)==0)
				{
					printf("Black wins");
				}
				else if(san_tiao(black)==0&&san_tiao(white)==1)
				{
					printf("White wins");
				}
				else if(san_tiao(black)==1&&san_tiao(white)==1)
				{
					if(santiao[0]>santiao[1])
					{
						printf("Black wins");
					}
					else if(santiao[0]<santiao[1])
					{
						printf("White wins");
					}
					else if(santiao[0]==santiao[1])
					{
						printf("Tie");
					}
				}
					else if(san_tiao(black)==0&&san_tiao(white)==0)
					{
						if(liang_dui(black)==1&&liang_dui(white)==0)
						{
							printf("Black wins");
						}
						else if(liang_dui(black)==0&&liang_dui(white)==1)
						{
							printf("White wins");
						}
						else if(liang_dui(black)==1&&liang_dui(white)==1)
						{
							if(max[0]>max[1])
							{
								printf("Black wins");
							}
							else if(max[0]<max[1])
							{
								printf("White wins");
							}
							else
							{
								if(min[0]>min[1])
								{
									printf("Black wins");
								}
								else if(min[0]<min[1])
								{
									printf("White wins");
								}
								else
								{
									printf("Tie");
								}
							}
						}
						else if(liang_dui(black)==0&&liang_dui(white)==0)
						{
							if(dui_zi(black)==1&&dui_zi(white)==0)
							printf("Black wins");
							else if(dui_zi(black)==0&&dui_zi(white)==1)
							{
								printf("White wins");
							}
							else if(dui_zi(black)==1&&dui_zi(white)==1)
							{
								if(duizi[0]>duizi[1])
								{
									printf("Black wins");
								}
								else if(duizi[0]<duizi[1])
								{
									printf("White wins");
								}
								else
								{
									if(index==1)
									{
										printf("Black wins");
									}
									else if(index==0)
									{
										printf("White wins");
									}
									else if(index==-1)
									{
										printf("Tie");
									}
								}
							}
							else if(dui_zi(black)==0&&dui_zi(white)==0)
							{
								if(index==1)
								{
									printf("Black wins");
								}
								else if(index==0)
								{
									printf("White wins");
								}
								else
								{
									printf("Tie");
								}
							}
						}
					}
				}
			}
		}

	return 0;
}