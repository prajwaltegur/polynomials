# polynomials

#include<stdio.h>
#include<string.h>
#include<math.h>

//function to convert array into integer coefficient
int arrtoint(int a[],int n)
{
 int i,integer=0;
 for(i=1;i<n;i++)
 {
 integer=10*integer+a[i];
 a[i]=0;
 }
 integer=integer*a[0];
 a[0]=0;
 return integer;
}



struct term
{
 int coef;
 char var[10];
};


int a[5];
char c[10];

void main()
{

 int b=0,d=0,e=0,j=0,i=0,k=0,varit=0,m;
 char exp[2][40];
 struct term res[10];
 struct term items[10]={0};
 char h[4]="end";
 
 
 clrscr();
 printf("enter the first expressions\n");
 scanf("%s",exp[0]);
 printf("enter the second expressions\n");
 scanf("%s", exp[1]);

label:
for(;j<2;j++)
 {
  label2:
  for(;;i++)
   {
    if(isdigit(exp[j][i])!=0)
     {
	    if(i==0)
	     {
	      a[0]=1;
	      b++;
	     }
      a[b]=exp[j][i] - '0';
      b++;
     }

   label3:
   if(exp[j][i]=='+'||exp[j][i]=='-'||exp[j][i]=='\0')
    {
      if(i==0 && exp[j][i]=='-')
       {
	      a[0]=-1;
	      b++;
	      i++;
	      goto label2;
       }

       else if(i==0 && exp[j][i]=='+')
       {
	      a[0]=1;
	      i++;
	      b++;
	      goto label2;
       }

       else if(exp[j][i]=='+')
       {
	      strncpy(items[d].var,c,varit);
	      items[d].coef=arrtoint(a,b);
	      d++;
	      a[0]=1;
	      varit=0;
	      b=1;
       }

       else if(exp[j][i]=='\0')
       {
	      strncpy(items[d].var,c,varit);
	      items[d].coef=arrtoint(a,b);
	      d++;
	      j++;
	      i=0;
	      varit=0;
	      goto label;
      }

     else if(exp[j][i]=='-')
     {
	    strncpy(items[d].var,c,varit);
	    items[d].coef=arrtoint(a,b);
	    d++;
	    a[0]=-1;
	    varit=0;
	    b=1;
     }
  }
 

   else if(isalpha(exp[j][i])!=0)
   {
    for(m=i;;m++)
    {
        if(exp[j][m]=='\0'||exp[j][m]=='+'||exp[j][m]=='-')
        {
          i=m;
          goto label3;
        }

	else
	{
	 c[varit]=exp[j][m];
	 varit++;
	}
    }
   }
  }
 }


 for(i=0;i<d;i++)
 {
  if(items[i].var==h)
  break;
  else
  {
   res[k].coef=items[i].coef;
   strcpy(res[k].var,items[i].var);
   for(j=i+1;j<d;j++)
   {
    if(items[j].var==h)
    break;
    else
    {
     if(strcmp(items[i].var,items[j].var)==0)
     {
      res[k].coef=res[k].coef+items[j].coef;
      strcpy(items[j].var,h);
     }
    }
   }
   k++;
  }
 }

 printf("\n\nThe result of the expression is\n");
 for(i=0;i<k;i++)
 {
  if(strcmp(res[i].var,h)!=0)
  {
   if(i==0)
    printf("%d%s ",res[i].coef,res[i].var);
   else
   {
    if(res[i].coef<0)
    printf("+ (%d)%s ",res[i].coef,res[i].var);
    else
    printf("+ %d%s ",res[i].coef,res[i].var);
   }
  }
 }

getch();
}
