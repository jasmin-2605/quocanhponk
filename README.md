# quocanhponk



// bai 1



#include <stdio.h>

int main ()
{
	int n,x,arr[100],b[100]={-1},t=0;
	printf("Nhap so phan tu mang a : ");
	scanf("%d",&n);
	printf("\nNhap mang A : ");
	for(int i=0;i<n;i++)
	{
		scanf("%d",&arr[i]);
		if(arr[i] % 2 == 0)
		{
			b[t++] = i;
		}
	}
	printf("\nNhap x ( x > 0) : ");
	scanf("%d",&x);
	int *p=b,*q=arr;
	printf("\na. Them x vao sau phan tu chan dau tien cua mang : ");
	if(*p >= 0)
	{
		for(int i=0;i<=*p;i++)
		{
			printf("%d ",*(q+i));
		}
		printf("%d ",x);
		for(int i= *p+1;i<n;i++)
		{
			printf("%d ",*(q+i));
		}
	} else if(*p < 0) printf("\nMang khong co phan tu chan ==> Khong the them x vao mang\n");
	printf("\n\nb. Xoa phan tu chan dau tien cua mang : ");
	if(*p >= 0)
	{
		for(int i=0;i<*p;i++)
		{
			printf("%d ",*(q+i));
		}
		for(int i= *p+1;i<n;i++)
		{
			printf("%d ",*(q+i));
		}
	} else if(*p <0) printf("\nMang khong co phan tu chan ==> Khong the xoa phan tu mang\n");
}


// bai 2

#include <stdio.h>

long long dq(int n)
{
	if(n==1) return 1;
	else if(n==2) return 2;
	else if(n==3) return 3;
	else return 2*dq(n-1)*(5*dq(n-2)+3*dq(n-3));
}
long long nor(int n)
{
	long long k1=1,k2=2,k3=3,kn;
	if(n >=4 )
	{
		for(int i=4;i<=n;i++)
		{
			kn=2*k3*(5*k2+3*k1);
			k1=k2;
			k2=k3;
			k3=kn;
		}
	}
	return kn;
}
main ()
{
	printf("a. Gia tri x7 = %lld\n",dq(7));
	int n;
	scanf("%d",&n);
	printf("DE quy %lld\n",dq(n));
	printf("THuong %lld",nor(n));
}


//bai 3

#include <stdio.h>
#include <math.h>
#define MAX 100


void nhapmt(int a[][MAX],int m,int n)
{
	for(int i=0;i<m;i++)
	{
		for(int j = 0;j<n;j++)
		{
			printf("Nhap gia tri a[%d][%d] : ",i,j);
			scanf("%d",&a[i][j]);
		}
	}
}

int kt(int n)
{
	if(n > 1)
	{
		int k=sqrt(n);
		if(k*k==n) return 1;
	}
	return 0;
}
int caua(int a[][MAX],int m,int n)
{
	int sum=0;
	for(int i=0;i<m;i++)
	{
		if(kt(a[i][0])==1)sum += a[i][0];
		if(kt(a[i][n-1])==1) sum+=a[i][n-1];
	
	}
	for(int j=1;j<n-1;j++)
	{
		if(kt(a[0][j])==1) sum+= a[0][j];
		if(kt(a[m-1][j])==1) sum+=a[m-1][j];
	}
return sum;
}
int caub(int a[][MAX],int m,int n)
{
	int sum[MAX]={0};
	int t=0,counter=0;
	for(int j=0;j<n;j++)
	{
		for(int i=0;i<m;i++)
		{
			sum[t]+=a[i][j];
		}
		if(sum[t] % 2 ==0) counter++;
		t++;
	}
	return counter;
}
int main ()
{
	int a[MAX][MAX],m,n;
	FILE *f;
	printf("\nnhap so dong,so cot ma tran:\n");	
    f=fopen("C:\\Users\\Admin\\Desktop\\table.inp.txt","wt");
    if(f==NULL){
    	printf("file khong ton tai");
    	return 0;
	}
    scanf("%d %d",&m,&n);
    fprintf(f,"%3d%3d \n",m,n);
    nhapmt(a,m,n);
    for (int i = 0; i < n; i++)
    {
        for (int j = 0; j < m; j++)
        
            fprintf(f,"%3d  ", a[i][j]);
           
        fprintf(f,"\n");
    }
    fclose(f);
    
    f=fopen("C:\\Users\\Admin\\Desktop\\table.out.txt","wt");
    fprintf(f,"Cau a: %d\n",caua(a,m,n));
    fprintf(f,"Cau b: %d\n",caub(a,m,n));
    fclose(f);
    
    
	
}
