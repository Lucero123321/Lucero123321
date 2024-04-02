#include <iostream>
#include <cmath>
#include <cstdlib>
#include <ctime>
using namespace std;
class numero
{
	protected:
		int n;
		int *y;
	private:
	public:
		numero (int);
		numero (const numero &);
		~numero();
		void llenar();
		void imprimir();
		friend class dos;
};
numero::numero (int n1=5):n(n1)
{
	y=new int [n];
}
numero::numero(const numero&w)
{
    int i;
	n=w.n;
	y=new int [n];
	for (i=0;i<n;i++)
    y[i]=w.y[i];
 }
numero::~numero ()
{
	delete []y;
}
void numero::llenar()
{
	int i;
	for (i=0;i<n;i++)
	y[i]=20+rand()%(43-20);
}
void numero::imprimir()
{
	int i;
	for (i=0;i<n;i++)
	cout<<y[i]<<endl;
}

class dos
{
protected:
	int x;
private:
public:
	dos (int);
	dos (const dos &);
	void exponente(numero &);
	void exponente1(numero );
	void exponente2();
};
dos::dos(int x1=5):x(x1)
{
}
dos::dos (const dos &w)
{
	x=w.x;
}
void dos::exponente(numero &z)
{
    int i,a[20];
    for (i=0;i<z.n;i++)
    {
    a[i]=pow(z.y[i],x);
    cout<<a[i]<<endl;
    }
}
void dos::exponente1(numero z)
{
    int i,a[20];
    for (i=0;i<z.n;i++)
    {
    a[i]=pow(z.y[i],x);
    cout<<a[i]<<endl;
    }
}
void dos::exponente2()
{
    numero z;
    int i,a[20];
    for (i=0;i<z.n;i++)
    {
    a[i]=pow(z.y[i],x);
    cout<<a[i]<<endl;
    }
}
int main ()
{
	srand(time (NULL));
	numero obj,obj1(6);
	cout<<endl<<"Sin parametros"<<endl;
	obj.llenar();
	obj.imprimir();
	dos a;
	cout<<"Sintaxis 1"<<endl;
	a.exponente(obj);
	cout<<"Sintaxis 2"<<endl;
	a.exponente1(obj);
	cout<<"Sintaxis 3"<<endl;
	a.exponente2();


	cout<<endl<<"Con parametros"<<endl;
	obj1.llenar();
	obj1.imprimir();
	cout<<"Sintaxis 1"<<endl;
	a.exponente(obj1);
	cout<<"Sintaxis 2"<<endl;
	a.exponente1(obj1);
	/*cout<<"Sintaxis 3"<<endl;
	a.exponente2(obj1);*/


    cout<<endl<<"Copia del sin parametros"<<endl;
	numero obj2(obj);
    obj2.imprimir();
	cout<<"Sintaxis 1"<<endl;
	a.exponente(obj2);
	cout<<"Sintaxis 2"<<endl;
	a.exponente1(obj2);
	/*cout<<"Sintaxis 3"<<endl;
	a.exponente2(obj2);*/
	return 0;
}
