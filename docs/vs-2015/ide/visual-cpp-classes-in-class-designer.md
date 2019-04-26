---
title: Clases de Visual C++ en el Diseñador de clases | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.inheritancelinelabel
helpviewer_keywords:
- Class Designer [Visual Studio], classes
ms.assetid: 75e56f8c-11ef-42a3-b7ec-3d2cf25c581b
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c1fb81261f52fa5aaf73c30579332779ae5bfa17
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443181"
---
# <a name="visual-c-classes-in-class-designer"></a>Clase de Visual C++ en el Diseñador de clases
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El Diseñador de clases admite las clases de C++ y visualiza las clases nativas de C++ igual que las formas de clase de Visual Basic y Visual C#, con la diferencia de que las clases de C++ pueden tener varias relaciones de herencia. Puede expandir la forma de clase para que muestre más campos y métodos de la clase o contraerla para ahorrar espacio.  
  
> [!NOTE]
> El Diseñador de clases no admite las uniones (un tipo especial de clase en la que la memoria asignada solo es la cantidad necesaria para el miembro de datos más grande de la unión).  
  
## <a name="simple-inheritance"></a>Herencia simple  
 Cuando se arrastra más de una clase a un diagrama de clases y las clases tienen una relación de herencia de clase, se conectan mediante una flecha. La flecha apunta en la dirección de la clase base. Por ejemplo, cuando las clases siguientes se muestran en un diagrama de clases, se conectan mediante una flecha que apunta de B a A:  
  
```  
class A {};  
class B : A {};  
```  
  
 También puede arrastrar únicamente la clase B al diagrama de clases, hacer clic con el botón derecho en la forma de clase de B y hacer clic en **Mostrar clases base**. De este modo se muestra su clase base: A.  
  
## <a name="multiple-inheritance"></a>Herencia múltiple  
 El Diseñador de clases admite la visualización de relaciones de herencia de varias clases. La *herencia múltiple* se usa cuando una clase derivada tiene atributos de más de una clase base. A continuación se muestra un ejemplo de herencia múltiple:  
  
```  
class Bird {};  
class Swimmer {};  
class Penguin : public Bird, public Swimmer {};  
```  
  
 Cuando se arrastra más de una clase al diagrama de clases y las clases tienen una relación de herencia de varias clases, se conectan mediante una flecha. La flecha apunta en la dirección de las clases base.  
  
 Si hace clic con el botón derecho en una forma de clase y, después, hace clic en **Mostrar clases base**, se muestran las clases base de la clase seleccionada.  
  
> [!NOTE]
> No se admite el comando **Mostrar clases derivadas** para el código de C++. Para mostrar las clases derivadas, vaya a Vista de clases, expanda el nodo de tipo, expanda la subcarpeta **Tipos derivados** y arrastre esos tipos al diagrama de clases.  
  
 Para más información sobre la herencia de varias clases, vea [(NO ESTÁ EN LA COMPILACIÓN) Herencia múltiple](http://msdn.microsoft.com/3b74185e-2beb-4e29-8684-441e51d2a2ca) y [Varias clases base](http://msdn.microsoft.com/library/a30c69fe-401c-4a87-96a0-e0da70c7c740).  
  
## <a name="abstract-classes"></a>Clases abstractas  
 El Diseñador de clases admite clases abstractas (también denominadas "clases base abstractas"). Se trata de clases de las que nunca se crean instancias, pero de las que se pueden derivar otras clases. Mediante un ejemplo de la anterior sección "Herencia múltiple" de este documento, puede crear instancias de la clase `Bird` como objetos individuales de la manera siguiente:  
  
```  
int main()  
{  
   Bird sparrow;  
   Bird crow;  
   Bird eagle;  
}  
```  
  
 Pero tal vez no piense crear instancias de la clase `Swimmer` como objetos individuales, sino simplemente derivar otros tipos de clases de animales, como `Penguin`, `Whale` y `Fish`. En ese caso, declararía la clase `Swimmer` como una clase base abstracta.  
  
 Para declarar una clase como abstracta, puede usar la palabra clave `abstract`. Los miembros marcados como abstractos o incluidos en una clase abstracta son virtuales y deben implementarse con clases que deriven de la clase abstracta.  
  
```  
class Swimmer abstract  
{  
   virtual void swim();  
   void dive();  
};  
```  
  
 También puede declarar una clase como abstracta si incluye al menos una función virtual pura:  
  
```  
class Swimmer  
{  
   virtual void swim() = 0;  
   void dive();  
};  
```  
  
 Al mostrar estas declaraciones en un diagrama de clases, el nombre de clase `Swimmer` y su función virtual pura `swim` aparecen en cursiva en una forma de clase abstracta, junto con la notación **Clase abstracta**. Observe que la forma del tipo de clase abstracta es igual que la de una clase normal, con la diferencia de que su borde es una línea de puntos.  
  
 Una clase derivada de una clase base abstracta debe invalidar todas las funciones virtuales puras de la clase base. De lo contrario, no se podrán crear instancias de la clase derivada. Así pues, por ejemplo, si deriva una clase `Fish` de la clase `Swimmer`, `Fish` debe invalidar el método `swim`:  
  
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
  
 Cuando este código se muestra en un diagrama de clases, el Diseñador de clases dibuja una línea de herencia de `Fish` a `Swimmer`.  
  
## <a name="anonymous-classes"></a>Clases anónimas  
 El Diseñador de clases admite las clases anónimas. Los *tipos de clase anónima* son clases declaradas sin un identificador. No pueden tener un constructor o un destructor, no se pueden pasar como argumentos a funciones y no se pueden devolver como valores devueltos de funciones. Puede usar una clase anónima para reemplazar un nombre de clase con un nombre de typedef, como en el ejemplo siguiente:  
  
```  
typedef struct  
{  
    unsigned x;  
    unsigned y;  
} POINT;  
```  
  
 Las estructuras también pueden ser anónimas. El Diseñador de clases muestra las clases y las estructuras anónimas del mismo modo que muestra el tipo respectivo. Aunque puede declarar y mostrar clases y estructuras anónimas, el Diseñador de clases no usará el nombre de etiqueta que usted especifique, sino que usará el nombre que genere la Vista de clases. La clase o estructura aparece en la Vista de clases y el Diseñador de clases como un elemento denominado **__unnamed**.  
  
 Para más información sobre las clases anónimas, vea [Tipos de clase anónima](http://msdn.microsoft.com/library/9ba667b2-8c2a-4c29-82a6-fa120b9233c8).  
  
## <a name="template-classes"></a>Clases de plantillas  
 El Diseñador de clases admite la visualización de clases de plantillas. Se admiten las declaraciones anidadas. En la tabla siguiente se muestran algunas declaraciones típicas.  
  
|elemento Code|Vista Diseñador de clases|  
|------------------|-------------------------|  
|`template <class T>`<br /><br /> `class A {};`|`A<T>`<br /><br /> Clase de plantilla|  
|`template <class T, class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> Clase de plantilla|  
|`template <class T, int i>`<br /><br /> `class A {};`|`A<T, i>`<br /><br /> Clase de plantilla|  
|`template <class T, template <class K> class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> Clase de plantilla|  
  
 En la tabla siguiente se muestran algunos ejemplos de especialización parcial.  
  
|Elemento de código|Vista Diseñador de clases|  
|------------------|-------------------------|  
|`template<class T, class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> Clase de plantilla|  
|`template<class T>`<br /><br /> `class A<T, T> {};`|`A<T, T>`<br /><br /> Clase de plantilla|  
|`template <class T>`<br /><br /> `class A<T, int> {};`|`A<T, int>`<br /><br /> Clase de plantilla|  
|`template <class T1, class T2>`<br /><br /> `class A<T1*, T2*> {};`|`A<T1*, T2*>`<br /><br /> Clase de plantilla|  
  
 En la tabla siguiente se muestran algunos ejemplos de herencia en especialización parcial.  
  
|Elemento de código|Vista Diseñador de clases|  
|------------------|-------------------------|  
|`template <class T, class U>`<br /><br /> `class A {};`<br /><br /> `template <class TC>`<br /><br /> `class A<T, int> {};`<br /><br /> `class B : A<int, float>`<br /><br /> `{};`<br /><br /> `class C : A<int, int>`<br /><br /> `{};`|`A<T, U>`<br /><br /> Clase de plantilla<br /><br /> `B`<br /><br /> Clase<br /><br /> (apunta a la clase A)<br /><br /> `C`<br /><br /> Clase<br /><br /> (apunta a la clase A)|  
  
 En la tabla siguiente se muestran algunos ejemplos de funciones de plantilla de especialización parcial.  
  
|Elemento de código|Vista Diseñador de clases|  
|------------------|-------------------------|  
|`class A`<br /><br /> `{`<br /><br /> `template <class T, class U>`<br /><br /> `void func(T a, U b);`<br /><br /> `template <class T>`<br /><br /> `void func(T a, int b);`<br /><br /> `};`|`A`<br /><br /> func\<T, U> (+ 1 sobrecarga)|  
|`template <class T1>`<br /><br /> `class A {`<br /><br /> `template <class T2>`<br /><br /> `class B {};`<br /><br /> `};`<br /><br /> `template<> template<>`<br /><br /> `class A<type>::B<type> {};`|`A<T1>`<br /><br /> Clase de plantilla<br /><br /> `B<T2>`<br /><br /> Clase de plantilla<br /><br /> (B se encuentra dentro de la clase A bajo **Tipos anidados**)|  
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `class A : C<int> {};`|`A`<br /><br /> Clase<br /><br /> -> C\<int><br /><br /> `C<T>`<br /><br /> Clase de plantilla|  
  
 En la tabla siguiente se muestran algunos ejemplos de herencia de plantilla.  
  
|Elemento de código|Vista Diseñador de clases|  
|------------------|-------------------------|  
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {`<br /><br /> `class B {};`<br /><br /> `}`<br /><br /> `class A : C<int>::B {};`|`A`<br /><br /> Clase<br /><br /> ->B<br /><br /> `C<int>`<br /><br /> Clase<br /><br /> (B se encuentra dentro de la clase C bajo **Tipos anidados**)<br /><br /> `C<T>`<br /><br /> Clase de plantilla|  
  
 En la tabla siguiente se muestran algunos ejemplos de conexión de clases especializadas canónicas.  
  
|Elemento de código|Vista Diseñador de clases|  
|------------------|-------------------------|  
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {};`<br /><br /> `class A : C<int> {};`<br /><br /> `class D : C<float> {};`|`A`<br /><br /> Clase<br /><br /> ->C\<int><br /><br /> `C<int>`<br /><br /> Clase<br /><br /> `C<T>`<br /><br /> Clase de plantilla<br /><br /> `D`<br /><br /> Clase<br /><br /> ->C\<float>|  
|`class B {`<br /><br /> `template <class T>`<br /><br /> `T min (const T &a, const T &b);`<br /><br /> `};`|`B`<br /><br /> min \<T>|  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con código de Visual C++ (Diseñador de clases)](../ide/working-with-visual-cpp-code-class-designer.md)   
 [Clases y structs](http://msdn.microsoft.com/library/516dd496-13fb-4f17-845a-e9ca45437873)   
 [Tipos de clase anónima](http://msdn.microsoft.com/library/9ba667b2-8c2a-4c29-82a6-fa120b9233c8)   
 [(NO ESTÁ EN LA COMPILACIÓN) Herencia múltiple](http://msdn.microsoft.com/3b74185e-2beb-4e29-8684-441e51d2a2ca)   
 [Varias clases base](http://msdn.microsoft.com/library/a30c69fe-401c-4a87-96a0-e0da70c7c740)   
 [Templates](http://msdn.microsoft.com/library/90fcc14a-2092-47af-9d2e-dba26d25b872) (Plantillas [C++])
