---
title: Fragmentos de código de Visual C++
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
ms.workload:
- cplusplus
ms.openlocfilehash: de27b201dadb23bb8209ebee24b34386f8fa5127
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62581765"
---
# <a name="visual-c-code-snippets"></a>Fragmentos de código de Visual C++

En Visual Studio se pueden usar fragmentos de código para agregar código de uso común a los archivos de código de C++. En general, los fragmentos de código se pueden usar de la misma manera que en C#, pero el conjunto predeterminado de fragmentos de código es diferente.

Hay dos opciones: agregar un fragmento de código en una ubicación concreta del código (inserción) o rodear el código seleccionado con un fragmento de código.

## <a name="insert-a-code-snippet"></a>Insertar un fragmento de código

Para insertar un fragmento de código, abra un archivo de código de C++ (*.cpp* o *.h*), haga clic en cualquier parte dentro del archivo y elija entre las acciones siguientes:

- Haga clic con el botón derecho para ver el menú contextual y seleccione **Insertar fragmento de código**.

- En el menú **Editar / IntelliSense**, seleccione **Insertar fragmento de código**.

- Use las teclas de acceso rápido: **Ctrl**+**K**+**X**

Verá una lista de opciones que empiezan por **#if**. Al seleccionar **#if**, verá el código siguiente agregado al archivo:

```cpp
#if 0

#endif // 0
```

A continuación, puede reemplazar el **0** por la condición correcta.

## <a name="use-a-code-snippet-to-surround-selected-code"></a>Usar un fragmento de código para rodear el código seleccionado

Para rodear el código seleccionado con un fragmento de código, seleccione una línea (o varias) y elija entre las acciones siguientes:

- Haga clic con el botón derecho para ver el menú contextual y seleccione **Envolver con**.

- En el menú **Edición** > **IntelliSense**, seleccione **Envolver con**.

- En un teclado, presione: **Ctrl**+**K**+**S**

Seleccione **#if**. Verá algo parecido a esto:

```cpp
#if 0
#include "pch.h"  // or whatever line you had selected
#endif // 0
```

A continuación, puede reemplazar el 0 por la condición correcta.

## <a name="where-can-i-find-a-complete-list-of-the-c-code-snippets"></a>¿Dónde puedo encontrar una lista completa de los fragmentos de código de C++?

Para ver la lista completa de los fragmentos de código de C++, vaya a **Administrador de fragmentos de código** (en el menú **Herramientas**) y establezca el **Lenguaje** en **Visual C++**. En la ventana inferior, expanda **Visual C++**. Verá los nombres de todos los fragmentos de código de C++ en orden alfabético.

La mayoría de los nombres de los fragmentos de código se explican por sí mismos, pero algunos pueden ser confusos.

## <a name="class-vs-classi"></a>Class frente a classi

El fragmento de código **class** proporciona la definición de una clase denominada `MyClass`, con el constructor y el destructor predeterminados adecuados, donde las definiciones de constructor y destructor se encuentran fuera de la clase:

```cpp
class MyClass
{
public:
    MyClass();
    ~MyClass();

private:

};

MyClass::MyClass()
{
}

MyClass::~MyClass()
{
}
```

El fragmento de código **classi** proporciona también la definición de una clase denominada `MyClass`, pero el constructor y el destructor predeterminados se definen en la definición de clase:

```cpp
class MyClass
{
public:
    MyClass()
    {
    }

    ~MyClass()
    {
    }

private:

};
```

## <a name="for-vs-forr-vs-rfor"></a>For frente a forr frente a rfor

Hay tres fragmentos de código **for** que proporcionan diferentes tipos de bucles `for`.

El fragmento de código **rfor** proporciona un bucle for [basado en rango](/cpp/cpp/range-based-for-statement-cpp) (vínculo). Esta construcción se prefiere a los bucles `for` basados en índice.

```cpp
for (auto& i : v)
{

}
```

El fragmento de código **for** proporciona un bucle `for` en el que la condición se basa en la longitud (en `size_t`) de un objeto.

```cpp
for (size_t i = 0; i < length; i++)
{

}
```

El fragmento de código **forr** proporciona un bucle `for` inverso en el que la condición se basa en la longitud (en enteros) de un objeto.

```cpp
for (int i = length - 1; i >= 0; i--)
{

}
```

## <a name="the-destructor-snippet-"></a>El fragmento de código de destructor (~)

El fragmento de código de destructor (**~**) muestra un comportamiento diferente según el contexto. Si se inserta este fragmento de código dentro de una clase, proporciona un destructor para esa clase. Por ejemplo, dado el siguiente código:

```cpp
class SomeClass {

};
```

Si se inserta el fragmento de código de destructor, proporciona un destructor para `SomeClass`:

```cpp
class SomeClass {
    ~SomeClass()
    {

    }
};
```

Si se intenta insertar el fragmento de destructor fuera de una clase, proporciona un destructor con un nombre de marcador de posición:

```cpp
~TypeNamePlaceholder()
{
```

## <a name="see-also"></a>Vea también

- [Fragmentos de código](../ide/code-snippets.md)