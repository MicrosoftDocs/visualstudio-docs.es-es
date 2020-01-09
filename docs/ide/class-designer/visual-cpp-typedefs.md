---
title: Definiciones de tipo de C++ en el Diseñador de clases
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.typedef
- vs.classdesigner.aliasofline
helpviewer_keywords:
- Class Designer [Visual Studio], typedefs
ms.assetid: c1984108-71fc-4d3a-b4d4-3eac2c6b4ebf
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 4c57382809b7730df2d7c674c24902d70ccab647
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590701"
---
# <a name="c-typedefs-in-class-designer"></a>Definiciones de tipo de C++ en el Diseñador de clases

Las instrucciones [TypeDef](/cpp/cpp/aliases-and-typedefs-cpp#typedefs) crean una o varias capas de direccionamiento indirecto entre un nombre y su tipo subyacente. El **Diseñador de clases** admite los tipos de definición de tipo de C++, que se declaran con la palabra clave `typedef`; por ejemplo:

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

## <a name="class-and-struct-shapes"></a>Formas de clase y estructura

En el **Diseñador de clases**, una definición de tipo de C++ tiene la forma del tipo especificado en la definición de tipo. Si el origen declara `typedef class`, la forma tiene esquinas redondeadas y la etiqueta **Class**. Para `typedef struct`, la forma tiene esquinas cuadradas y la etiqueta **Struct**.

Las clases y estructuras pueden tener definiciones de tipo anidadas que estén declaradas dentro de ellas. En el **Diseñador de clases**, las formas de clase y estructura pueden mostrar declaraciones de definición de tipo anidadas como formas anidadas.

Las formas de TypeDef admiten los comandos **Mostrar como asociación** y **Mostrar como asociación de colecciones** en el menú contextual.

### <a name="class-typedef-example"></a>Ejemplo de definición de tipo de clase

```cpp
class B {};
typedef B MyB;
```

![Definición de tipo de clase de C++ en el Diseñador de clases](media/cpp-class-typedef.png)

### <a name="struct-typedef-example"></a>Ejemplo de definición de tipo de estructura

```cpp
typedef struct mystructtag
{
    int   i;
    double f;
} mystruct;
```

![Definición de tipo de estructura de C++ en el Diseñador de clases](media/cpp-struct-typedef.png)

## <a name="unnamed-typedefs"></a>Definiciones de tipo sin nombre

Aunque se puede declarar una definición de tipo sin nombre, el **Diseñador de clases** no usará el nombre de etiqueta que se especifique. El **Diseñador de clases** usa el nombre que genera **Vista de clases**. Por ejemplo, la siguiente declaración es válida, pero aparece en la **Vista de clases** y en el **Diseñador de clases** como un objeto denominado **__unnamed**:

```cpp
typedef class coord
{
   void P(x,y);
   unsigned x;
   unsigned y;
};
```

> [!NOTE]
> El **Diseñador de clases** no muestra ninguna definición de tipo cuyo tipo de origen es un puntero de función.

## <a name="see-also"></a>Vea también

- [Trabajo con código de C++](working-with-visual-cpp-code.md)
- [Typedefs](/cpp/cpp/aliases-and-typedefs-cpp#typedefs)
