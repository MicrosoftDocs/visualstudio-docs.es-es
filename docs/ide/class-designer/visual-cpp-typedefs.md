---
title: "Definiciones de tipos de Visual C++ en el Diseñador de clases | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.classdesigner.typedef
- vs.classdesigner.aliasofline
helpviewer_keywords:
- Class Designer [Visual Studio], typedefs
ms.assetid: c1984108-71fc-4d3a-b4d4-3eac2c6b4ebf
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 96d7e8cee6ce024040184aca50b5f5cb6facf388
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2018
---
# <a name="visual-c-typedefs-in-class-designer"></a>Definiciones de tipos de Visual C++ en el Diseñador de clases
Las instrucciones TypeDef crean una o más capas de direccionamiento indirecto entre un nombre y su tipo subyacente. El Diseñador de clases admite los tipos de definición de tipos de C++, que se declaran con la palabra clave `typedef`, por ejemplo:  
  
```cpp
typedef class coord  
{  
   void P(x,y);  
   unsigned x;  
   unsigned y;  
} COORD;  
```  
  
A continuación, puede usar este tipo para declarar una instancia:  
  
`COORD OriginPoint;`  
  
Aunque se puede declarar una definición de tipo sin nombre, el Diseñador de clases no usará el nombre de etiqueta que especifique; usará el nombre que genera la vista de clases. Por ejemplo, la siguiente declaración es válida, pero aparece en la vista de clases y en el Diseñador de clases como un objeto denominado **__unnamed**:  
  
```cpp
typedef class coord  
{  
   void P(x,y);  
   unsigned x;  
   unsigned y;  
};  
```

Para más información sobre cómo usar el tipo `typedef`, vea [Typedefs](/cpp/aliases-and-typedefs-cpp#typedefs).

Una forma de definición de tipos de C++ tiene la forma del tipo especificado en la definición de tipo. Por ejemplo, si el origen declara `typedef class`, la forma tiene esquinas redondeadas y la etiqueta **Class**. Para `typedef struct`, la forma tiene esquinas cuadradas y la etiqueta **Struct**.  
  
Las clases y estructuras pueden tener definiciones de tipos anidadas declaradas en ellas; por lo tanto, las formas de clase y estructura pueden mostrar las definiciones de tipos anidadas como formas anidadas.  
  
Las formas de TypeDef admiten los comandos **Mostrar como asociación** y **Mostrar como asociación de colecciones** en el menú contextual.  
  
Estos son algunos ejemplos de tipos de TypeDef que admite el Diseñador de clases:  
  
`typedef type name`  
  
*name* : *type*  
  
typedef  
  
Dibuja una línea de asociación que se conecta al tipo *name*, si es posible.  
  
`typedef void (*func)(int)`  
  
`func: void (*)(int)`  
  
typedef  
  
TypeDef para punteros de función. No se dibuja ninguna línea de asociación.  
  
El Diseñador de clases no muestra una definición de tipos si su tipo de origen es un puntero de función.  
  
```cpp
typedef int MyInt;  
class A {  
   MyInt I;  
};  
```  
  
`MyInt: int`  
  
typedef  
  
`A`  
  
Clase  
  
Dibuja una línea de asociación que señala desde la forma del tipo de origen a la forma del tipo de destino.  
  
`Class B {};`  
  
`typedef B MyB;`  
  
`B`  
  
Clase  
  
`MyB : B`  
  
typedef  
  
Al hacer clic con el botón derecho en una forma de definición de tipos y en **Mostrar como asociación**, se muestra la definición de tipos o la clase y una línea de **Alias de** que une las dos formas (similar a una línea de asociación).  
  
`typedef B MyB;`  
  
`typedef MyB A;`  
  
`MyBar : Bar`  
  
typedef  
  
Como anteriormente.  
  
```cpp
Class B {};  
typedef B MyB;  
  
class A {  
   MyB B;  
};  
```  
  
`B`  
  
Clase  
  
`MyB : B`  
  
typedef  
  
`A`  
  
Clase  
  
`MyB` es una forma de definición de tipos anidados.  
  
`#include <vector>`  
  
`...`  
  
`using namespace std;`  
  
`...`  
  
`typedef vector<int> MyIntVect;`  
  
`vector<T>`Class  
  
`MyIntVect : vector<int>`  
  
typedef  
  
`class B {};`  
  
`typedef B MyB;`  
  
`class A : MyB {};`  
  
`MyB : B`  
  
typedef  
  
-> B  
  
`B`  
  
`A`  
  
Clase  
  
-> MyB  
  
El Diseñador de clases no admite la visualización de este tipo de relación mediante un comando de menú contextual.  
  
`#include <vector>`  
  
`Typedef MyIntVect std::vector<int>;`  
  
`Class MyVect : MyIntVect {};`  
  
`std::vector<T>`  
  
Clase  
  
`MyIntVect : std::vector<int>`  
  
typedef  
  
`MyVect`  
  
Clase  
  
-> MyIntVect  
  
## <a name="see-also"></a>Vea también

[Trabajar con código de Visual C++](working-with-visual-cpp-code.md)  
[Typedefs](/cpp/aliases-and-typedefs-cpp#typedefs)