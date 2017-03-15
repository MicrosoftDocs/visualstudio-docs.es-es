---
title: "Visual C++ Classes in Class Designer | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.classdesigner.inheritancelinelabel"
helpviewer_keywords: 
  - "Class Designer [Visual Studio], classes"
ms.assetid: 75e56f8c-11ef-42a3-b7ec-3d2cf25c581b
caps.latest.revision: 19
caps.handback.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Visual C++ Classes in Class Designer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El Diseñador de clases admite las clases de C\+\+ y visualiza las clases nativas de C\+\+ del mismo modo que Visual Basic y las formas de clase de Visual C\#, con la salvedad de que las clases de C\+\+ pueden tener varias relaciones de herencia.  Puede expandir la forma de clase para mostrar más campos y métodos de la clase, o contraerla para ahorrar espacio.  
  
> [!NOTE]
>  El Diseñador de clases no admite las uniones \(un tipo especial de clase en el que la memoria asignada es solamente la cantidad necesaria para el miembro de datos más grande de la unión\).  
  
## Herencia simple  
 Si se arrastra más de una clase a un diagrama de clases y las clases tienen una relación de herencia de clases, una flecha las conecta.  La flecha apunta en la dirección de la clase base.  Por ejemplo, cuando las clases siguientes se muestran en un diagrama de clases, una flecha las conecta, apuntando desde B hasta A:  
  
```  
class A {};  
class B : A {};  
```  
  
 También puede arrastrar únicamente la clase B hasta el diagrama de clases, hacer clic con el botón secundario en la forma de clase para B y, a continuación, hacer clic en **Mostrar clases base**.  De esta forma, se muestra la clase base, es decir, A.  
  
## Herencia múltiple  
 El Diseñador de clases admite la visualización de relaciones de herencia múltiple de clases.  La *herencia múltiple* se usa cuando una clase derivada presenta atributos de más de una clase base.  A continuación, se muestra un ejemplo de herencia múltiple:  
  
```  
class Bird {};  
class Swimmer {};  
class Penguin : public Bird, public Swimmer {};  
```  
  
 Si se arrastra más de una clase al diagrama de clases y las clases tienen una relación de herencia múltiple de clases, una flecha las conecta.  La flecha apunta en la dirección de las clases base.  
  
 Al hacer clic con el botón secundario en una forma de clase y, a continuación, hacer clic en **Mostrar clases base** se muestran las clases base para la clase seleccionada.  
  
> [!NOTE]
>  El código de C\+\+ no admite el comando **Mostrar clases derivadas**.  Puede mostrar las clases derivadas yendo a Vista de clases, expandiendo el nodo de tipo, expandiendo la subcarpeta **Tipos derivados** y, a continuación, arrastrando esos tipos hasta el diagrama de clases.  
  
 Para obtener más información acerca de la herencia múltiple de clases, consulte [Herencia múltiple](http://msdn.microsoft.com/es-es/3b74185e-2beb-4e29-8684-441e51d2a2ca) y [Varias clases base](/visual-cpp/cpp/multiple-base-classes).  
  
## Clases abstractas  
 El Diseñador de clases admite clases abstractas \(también denominadas "clases base abstractas"\).  Éstas son clases de las que nunca crea instancias, pero de las que puede derivar otras clases.  Utilizando un ejemplo de "Herencia múltiple" mencionado anteriormente en este documento, puede crear instancias de la clase `Bird` como objetos individuales del modo siguiente:  
  
```  
int main()  
{  
   Bird sparrow;  
   Bird crow;  
   Bird eagle;  
}  
```  
  
 Sin embargo, no puede crear instancias de la clase `Swimmer` como objetos individuales.  Sólo puede derivar otros tipos de clases de animales de ella, por ejemplo, `Penguin`, `Whale` y `Fish`.  En ese caso, puede declarar la clase `Swimmer` como una clase base abstracta.  
  
 Para declarar una clase como abstracta, puede utilizar la palabra clave `abstract`.  Los miembros que están marcados como abstractos o que se incluyen en una clase abstracta, son virtuales y deben ser implementados por clases derivadas de la clase abstracta.  
  
```  
class Swimmer abstract  
{  
   virtual void swim();  
   void dive();  
};  
```  
  
 También puede declarar una clase como abstracta incluyendo al menos una función virtual pura:  
  
```  
class Swimmer  
{  
   virtual void swim() = 0;  
   void dive();  
};  
```  
  
 Al mostrar estas declaraciones en un Diagrama de clases, el nombre de clase `Swimmer` y su función virtual pura `swim` aparecen en cursiva en una forma de clase abstracta, junto con la notación **Clase abstracta**.  Observe que la forma del tipo de clase abstracta es la misma que la de una clase normal, excepto que su borde es una línea de puntos.  
  
 Una clase derivada de una clase base abstracta debe invalidar cada función virtual pura en la clase base o no se podrán crear instancias de la clase derivada.  Por ejemplo, si deriva una clase `Fish` de la clase `Swimmer`, `Fish` debe invalidar el método `swim`:  
  
```  
class Fish : public Swimmer  
{  
   void swim(int speed);  
};  
  
int main()  
{  
   Fish guppy;  
}  
```  
  
 Al mostrar este código en un Diagrama de clases, el Diseñador de clases dibuja una línea de herencia de `Fish` en `Swimmer`.  
  
## Clases anónimas  
 El Diseñador de clases admite las clases anónimas.  Los *tipos de clases anónimas* son clases declaradas sin identificador.  No pueden tener ningún constructor ni destructor, no pueden pasarse como argumentos a funciones y no pueden devolverse como valores devueltos de funciones.  Puede usar una clase anónima para reemplazar un nombre de clase por un nombre de definición de tipos, tal y como se muestra en el ejemplo siguiente:  
  
```  
typedef struct  
{  
    unsigned x;  
    unsigned y;  
} POINT;  
```  
  
 Las estructuras también pueden ser anónimas.  El Diseñador de clases muestra las clases y estructuras anónimas del mismo modo que muestra el tipo respectivo.  Aunque puede declarar y mostrar clases y estructuras anónimas, el Diseñador de clases no usará el nombre de etiqueta que especifique.  Usará el nombre generado por la Vista de clases.  La clase o estructura se mostrará en la Vista de clases y en el Diseñador de clases como un elemento denominado **\_\_unnamed**.  
  
 Para obtener más información acerca de las clases anónimas, consulte [Tipos de clase anónima](/visual-cpp/cpp/anonymous-class-types).  
  
## Clases de plantillas  
 El Diseñador de clases admite la visualización de clases de plantillas.  Se admiten declaraciones anidadas.  En la tabla siguiente se muestran algunas declaraciones típicas.  
  
|Elemento de código|Vista Diseñador de clases|  
|------------------------|-------------------------------|  
|`template <class T>`<br /><br /> `class A {};`|`A<T>`<br /><br /> Clase de plantilla|  
|`template <class T, class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> Clase de plantilla|  
|`template <class T, int i>`<br /><br /> `class A {};`|`A<T, i>`<br /><br /> Clase de plantilla|  
|`template <class T, template <class K> class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> Clase de plantilla|  
  
 En la tabla siguiente se muestran algunos ejemplos de especialización parcial.  
  
|Elemento de código|Vista Diseñador de clases|  
|------------------------|-------------------------------|  
|`template<class T, class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> Clase de plantilla|  
|`template<class T>`<br /><br /> `class A<T, T> {};`|`A<T, T>`<br /><br /> Clase de plantilla|  
|`template <class T>`<br /><br /> `class A<T, int> {};`|`A<T, int>`<br /><br /> Clase de plantilla|  
|`template <class T1, class T2>`<br /><br /> `class A<T1*, T2*> {};`|`A<T1*, T2*>`<br /><br /> Clase de plantilla|  
  
 En la tabla siguiente se muestran algunos ejemplos de herencia en la especialización parcial.  
  
|Elemento de código|Vista Diseñador de clases|  
|------------------------|-------------------------------|  
|`template <class T, class U>`<br /><br /> `class A {};`<br /><br /> `template <class TC>`<br /><br /> `class A<T, int> {};`<br /><br /> `class B : A<int, float>`<br /><br /> `{};`<br /><br /> `class C : A<int, int>`<br /><br /> `{};`|`A<T, U>`<br /><br /> Clase de plantilla<br /><br /> `B`<br /><br /> Clase<br /><br /> \(apunta a Clase A\)<br /><br /> `C`<br /><br /> Clase<br /><br /> \(apunta a Clase A\)|  
  
 En la tabla siguiente se muestran algunos ejemplos de funciones de plantilla de especialización parcial.  
  
|Elemento de código|Vista Diseñador de clases|  
|------------------------|-------------------------------|  
|`class A`<br /><br /> `{`<br /><br /> `template <class T, class U>`<br /><br /> `void func(T a, U b);`<br /><br /> `template <class T>`<br /><br /> `void func(T a, int b);`<br /><br /> `};`|`A`<br /><br /> func\<T, U\> \(\+ 1 sobrecarga\)|  
|`template <class T1>`<br /><br /> `class A {`<br /><br /> `template <class T2>`<br /><br /> `class B {};`<br /><br /> `};`<br /><br /> `template<> template<>`<br /><br /> `class A<type>::B<type> {};`|`A<T1>`<br /><br /> Clase de plantilla<br /><br /> `B<T2>`<br /><br /> Clase de plantilla<br /><br /> \(B se encuentra dentro de la clase A, bajo **Tipos anidados**\)|  
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `class A : C<int> {};`|`A`<br /><br /> Clase<br /><br /> \-\> C\<int\><br /><br /> `C<T>`<br /><br /> Clase de plantilla|  
  
 En la tabla siguiente se muestran algunos ejemplos de herencia de plantillas.  
  
|Elemento de código|Vista Diseñador de clases|  
|------------------------|-------------------------------|  
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {`<br /><br /> `class B {};`<br /><br /> `}`<br /><br /> `class A : C<int>::B {};`|`A`<br /><br /> Clase<br /><br /> \-\>B<br /><br /> `C<int>`<br /><br /> Clase<br /><br /> \(B se encuentra dentro de la clase C, bajo **Tipos anidados**\)<br /><br /> `C<T>`<br /><br /> Clase de plantilla|  
  
 En la tabla siguiente se muestran algunos ejemplos de conexión de clases especializadas canónicas.  
  
|Elemento de código|Vista Diseñador de clases|  
|------------------------|-------------------------------|  
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {};`<br /><br /> `class A : C<int> {};`<br /><br /> `class D : C<float> {};`|`A`<br /><br /> Clase<br /><br /> \-\>C\<int\><br /><br /> `C<int>`<br /><br /> Clase<br /><br /> `C<T>`<br /><br /> Clase de plantilla<br /><br /> `D`<br /><br /> Clase<br /><br /> \-\>C\<float\>|  
|`class B {`<br /><br /> `template <class T>`<br /><br /> `T min (const T &a, const T &b);`<br /><br /> `};`|`B`<br /><br /> min \<T\>|  
  
## Vea también  
 [Working with Visual C\+\+ Code \(Class Designer\)](../ide/working-with-visual-cpp-code-class-designer.md)   
 [Clases y structs](/visual-cpp/cpp/classes-and-structs-cpp)   
 [Tipos de clase anónima](/visual-cpp/cpp/anonymous-class-types)   
 [Herencia múltiple](http://msdn.microsoft.com/es-es/3b74185e-2beb-4e29-8684-441e51d2a2ca)   
 [Varias clases base](/visual-cpp/cpp/multiple-base-classes)   
 [Plantillas](/visual-cpp/cpp/templates-cpp)