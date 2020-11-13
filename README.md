# Teorema de pitagoras

## Pseudocódigo

```

```

## Código

```c++

#include <iostream>

using namespace std;

extern double raiz_cuadrada(double numero, double aproximacion, int contador);
extern double opuesto(double hipotenusa, double adyacente);
extern double adyacente(double hipotenusa, double opuesto);
extern double hipotenusa(double opuesto, double adyacente);

int main()
{
	double op, ady, hip, resultado;
	int opciones;
	bool bandera = true;

  cout << "Elija que desea encontrar:\n";
	cout << "1. Opuesto\n";
	cout << "2. Adyacente\n";
	cout << "3. Hipotenusa\n";

	do
	{
		cin >> opciones;
		if (opciones > 0 && opciones < 4)
		{
			bandera = false;
		}
		else
		{
			cout << "Por favor elija una opcion: 1,2 o 3\n";
			cin.clear();
			cin.ignore(numeric_limits<streamsize>::max(), '\n');
		}
	} while (bandera);

	switch (opciones)
	{
	case 1:
		//Opuesto
		bandera = true;
		do
		{
			// Ingresar la hipotenusa
			cout << "Ingrese la hipotenusa \n";
			cin >> hip;
			if (hip > 0)
			{
				bandera = false;
			}
			else {
				cout << "Por favor ingrese un numero\n";
				cin.clear();
				cin.ignore(numeric_limits<streamsize>::max(), '\n');
			}
		} while (bandera);
		bandera = true;
		do
		{
			// Ingresar la adyacente
			cout << "Ingrese el cateto adyacente \n";
			cin >> ady;
			if (ady > 0)
			{
				bandera = false;
			}
			else {
				cout << "Por favor ingrese un numero\n";
				cin.clear();
				cin.ignore(numeric_limits<streamsize>::max(), '\n');
			}
		} while (bandera);
		resultado = opuesto(hip, ady);
		break;
	case 2:
		//Adyacente
		bandera = true;
		do
		{
			// Ingresar la hipotenusa
			cout << "Ingrese la hipotenusa \n";
			cin >> hip;
			if (hip > 0)
			{
				bandera = false;
			}
			else {
				cout << "Por favor ingrese un numero\n";
				cin.clear();
				cin.ignore(numeric_limits<streamsize>::max(), '\n');
			}
		} while (bandera);
		bandera = true;
		do
		{
			// Ingresar la opuesto
			cout << "Ingrese el cateto opuesto \n";

			cin >> ady;
			if (ady > 0)
			{
				bandera = false;
			}
			else {
				cout << "Por favor ingrese un numero\n";
				cin.clear();
				cin.ignore(numeric_limits<streamsize>::max(), '\n');
			}
		} while (bandera);
		resultado = adyacente(hip, ady);
		break;
	case 3:
		//Hipotenusa
		bandera = true;
		do
		{
			// Ingresar la hipotenusa
			cout << "Ingrese el cateto opuesto\n";
			cin >> op;
			if (op > 0)
			{
				bandera = false;
			}
			else {
				cout << "Por favor ingrese un numero\n";
				cin.clear();
				cin.ignore(numeric_limits<streamsize>::max(), '\n');
			}
		} while (bandera);
		bandera = true;
		do
		{
			// Ingresar la opuesto
			cout << "Ingrese el cateto adyacente\n";
			cin >> ady;
			if (ady > 0)
			{
				bandera = false;
			}
			else {
				cout << "Por favor ingrese un numero\n";
				cin.clear();
				cin.ignore(numeric_limits<streamsize>::max(), '\n');
			}
		} while (bandera);
		resultado = hipotenusa(op, ady);
		break;
	}

	cout << "\n";
	cout << "El resultado es: " << resultado << "\n";
	system("PAUSE");

	return 0;
}


double raiz_cuadrada(double numero, double aproximacion, int contador)
{
	if (numero <= 0)
	{
		return 0;
	}
	double preaproximacion = aproximacion;

	// Por Newton-Raphson x_(n+1) = x_(n) - f(x_(n))/f'(x_(n))
	// f(x_(n)) = x^2 - numero = 0
	aproximacion = aproximacion - ((aproximacion * aproximacion) - numero) / (2 * aproximacion);

	if (aproximacion == preaproximacion || contador > 60)
	{
		return aproximacion;
	}
	return raiz_cuadrada(numero, aproximacion, ++contador);
}
double opuesto(double hipotenusa, double adyacente)
{
	double cuadrado = hipotenusa * hipotenusa - adyacente * adyacente;
	return raiz_cuadrada(cuadrado, 1, 0);
}
double adyacente(double hipotenusa, double opuesto)
{
	double cuadrado = hipotenusa * hipotenusa - opuesto * opuesto;
	return raiz_cuadrada(cuadrado, 1, 0);
}
double hipotenusa(double opuesto, double adyacente)
{
	double cuadrado = opuesto * opuesto + adyacente * adyacente;
	return raiz_cuadrada(cuadrado, 1, 0);
}

```
