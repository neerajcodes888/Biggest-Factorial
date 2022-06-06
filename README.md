#include<iostream>
using namespace std;
#define max 50000
int multiply(int x,int result[],int result_size)
{
    int carry=0;
    for(int i=0;i<result_size;i++)
    {
        int product=result[i]*x+carry;
        result[i]=product%10;
        carry=product/10;
    }
    while(carry)
    {
        result[result_size]=carry%10;
        carry=carry/10;
        result_size++;
    }
    return result_size;
}
void factorial(int n)
{
    int result[max],c=0;;
    result[0]=1;
    int result_size=1;
    for(int i=2;i<=n;i++)
    {
        result_size=multiply(i,result,result_size);
    }
    cout<<"Factorial of "<<n<<" will be "<<endl;
    for(int i=result_size-1;i>=0;i--)
    {
        cout<<result[i];
        c++;
    }
    cout<<endl<<"No. of digits:"c;
}
int main()
{
    int n;
    cout<<"Enter any number to get its Factorial:";
    cin>>n;
    factorial(n);
}
