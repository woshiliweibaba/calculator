#include <stdio.h>
#include <stdlib.h>
#include <string.h>

char ch={0};

int numarr[30];
int num_i=0;
int fn=0;
char tnsarr[30];
int tnsa_i=0;
char jsarr[30];
int jsa_i=0;
int tcnarr[30];
int tcna_i=0;
char csarr[30];
int csa_i=0;
int isj=0;
int tfn=0;


void Count(void);
void setJstr(void);
void setCstr(void);
void setKstr(void);
void setNumberstr(char ch);
void iniTsarr(void);
void countC();
void inic();
void finish(void);
void iniAll(void);

int main(void)
{
	
	 system("cls");
	 
	 printf("********************C语言简易计算器********************\n|             时间:2017年11月22日00:00:00             |\n|                  e 结束运行                         |\n|                    操作符:                          |\n|                        +(加)                        |\n|                             -(减)                   |\n|                                  *(乘)              |\n|                                        /(除)        |\n*******************************************************\n");
	 
	 
	while(1)
	{
	printf("                    ");
	Count();
	if('\0'!=tnsarr[0]||'\0'!=jsarr[0])
	{
				printf("= %d\n",fn);
	}

	
	

	iniAll();
	}
	return 0;
}

void Count()
{


	while(1)
	{
		ch=getch();

		if('*'==ch||'/'==ch){
		
		setCstr();
		}
		
		
		if('+'==ch||'-'==ch)
		
		setJstr();
		
		
		if(ch>=48&&ch<=57)
		
		setNumberstr(ch);
		
		if('e'==ch)
		exit(0);
		
		
		if('='==ch||'\r'==ch)
		{
			
			numarr[num_i]=atoi(tnsarr);
			++num_i;
			
	
			break;
		}
		
		
	}
	
	finish();
	
	return ;
}


void setJstr(){
	
	printf("%c",ch);
	if(0==isj)
	{
	numarr[num_i]=atoi(tnsarr);
	++num_i;
	}
	isj=0;
	iniTsarr();
	jsarr[jsa_i]=ch;
	++jsa_i;
	
	return;
}


void setCstr()
{
	printf("%c",ch);
	
	tcnarr[tcna_i]=atoi(tnsarr);
	++tcna_i;
	iniTsarr();
	csarr[csa_i]=ch;
	++csa_i;
	
	countC();
	
	return;
}
void countC(){
	
	
	while(1)
	{
		ch=getch();
		if(ch>=48&&ch<=57)
			setNumberstr(ch);
		if('*'==ch||'/'==ch)
		{
			setCstr();
			return;
		}
			
			
		if('='==ch||'\r'==ch||'+'==ch||'-'==ch)
		{
			
			int i;
			tfn=tcnarr[0];
			
			for(i=0;i<tcna_i;++i)
			{
			
				if('*'==csarr[i])
					{
				
						
					tfn*=tcnarr[i+1];
					}
				if('/'==csarr[i])
					tfn/=tcnarr[i+1];
			}
			isj=1;
			break;
		}
	}
	 
		numarr[num_i]=tfn;
		++num_i;
		inic();
		return;
}



void setNumberstr(char c){
	printf("%c",ch);
	tnsarr[tnsa_i]=c;
	++tnsa_i;
	
	return;
}



void iniTsarr()
{
	tnsa_i=0;
	memset(tnsarr,'\0',30*sizeof(char));
	return;
}


void finish()
{
	int i=0;
	fn=numarr[0];

	for(i=0;i<num_i;++i)
	{

		
		if('+'==jsarr[i])
		{
	
			fn+=numarr[i+1];
		}
		if('-'==jsarr[i])
		{
		
			fn-=numarr[i+1];
		}
		
	}
	return;	
}


void iniAll(void)
{
	memset(numarr,0,sizeof(int)*30);
	num_i=0;
	fn=0;
	memset(tnsarr,'\0',sizeof(char)*30);
	tnsa_i=0;
	memset(jsarr,'\0',sizeof(char)*30);
	jsa_i=0;
	memset(csarr,'\0',sizeof(char)*30);
	csa_i=0;
	
	isj=0;
	
	return;
}

void inic()
{
	memset(tcnarr,0,sizeof(int)*30);
	tcna_i=0;
	memset(csarr,0,sizeof(char)*30);
	csa_i=0;
	tfn=0;
	return;
	}
