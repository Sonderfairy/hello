# hello
My first repository on Github
#include <stdio.h>
#include <stdlib.h>
#define   N   8
struct  slist
{  double   s;
   struct slist  *next;
};
typedef  struct slist  STREC;
double  fun( STREC *h  )
{
   double ave=0.0;
   STREC *p=h->next;
   while(p!=NULL)
   {
   	ave=ave+p->s;
   	p=p->next;
   }
   return ave/N;
}
//求链表中数据域的平均值，应首先使用循环语句遍历链表，求各节点数据域中数值的和
//遍历链表时应定义一个指向结点的指针p,因为头结点中没有数值，所以直接指向头结点的下一个结点
 //链表数据域的遍历是固定用法 

STREC * creat( double *s)
{ STREC  *h,*p,*q;   int  i=0;
  h=p=(STREC*)malloc(sizeof(STREC));p->s=0;
  while(i<N)
  { q=(STREC*)malloc(sizeof(STREC));
    q->s=s[i]; i++;  p->next=q; p=q;
  }
  p->next=0;
  return  h;
}
void outlist( STREC *h)
{ STREC *p;
  p=h->next; printf("head");
  do
  { printf("->%4.1f",p->s);p=p->next;}
  while(p!=0);
  printf("\n\n");
}
main()
{  double  s[N]={85,76,69,85,91,72,64,87},ave;
   void NONO (  );
   STREC  *h;
   h=creat( s );   outlist(h);
   ave=fun( h );
   printf("ave= %6.3f\n",ave);
   NONO();
}
void NONO()
{/* 本函数用于打开文件，输入数据，调用函数，输出数据，关闭文件。 */
  FILE *in, *out ;
  int i,j ; double  s[N],ave;
  STREC *h ;
  in = fopen("..\\in.dat","r") ;
  out = fopen("..\\out.dat","w") ;
  for(i = 0 ; i < 10 ; i++) {
    for(j=0 ; j < N; j++) fscanf(in, "%lf,", &s[j]) ;
    h=creat( s );
    ave=fun( h );
    fprintf(out, "%6.3lf\n", ave) ;    
  }
  fclose(in) ;
  fclose(out) ;
}
