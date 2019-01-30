---
title: Fragmentos de código
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- vs.ExpansionManagerImport
- vs.codesnippetmanager
helpviewer_keywords:
- surround with
- code snippets
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: 3b18f716c1804b0217fd8c882e152de0352a72ab
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54958347"
---
# <a name="code-snippets"></a>Fragmentos de código

Los fragmentos de código son pequeños bloques de código reutilizable que se pueden insertar en un archivo de código mediante un comando de menú contextual o una combinación de teclas de acceso rápido. Normalmente contienen bloques de código usados con mucha frecuencia, como bloques `try-finally` o `if-else`, pero pueden usarse también para insertar clases o métodos completos.

> [!NOTE]
> Este tema se aplica a Visual Studio para Windows. En el caso de Visual Studio para Mac, vea [Fragmentos de código (Visual Studio para Mac)](/visualstudio/mac/snippets).

Hay fragmentos de código disponibles para una gran variedad de lenguajes, entre otros, C#, C++, Visual Basic, XML y T-SQL. Para ver todos los fragmentos de código instalados disponibles de un lenguaje, abra el **Administrador de fragmentos de código** desde el menú **Herramientas** en Visual Studio y elija el lenguaje en la parte superior del menú desplegable.

![Cuadro de diálogo Administrador de fragmentos de código](media/code-snippets-manager.png)

Estas son las formas en general de tener acceso a los fragmentos de código:

- En la barra de menús, elija **Edición** > **IntelliSense** > **Insertar fragmento de código**.

- En el menú contextual del editor de código, elija **Fragmento de código** > **Insertar fragmento de código**.

- En el teclado, presione **Ctrl**+**K**+**X**.

## <a name="expansion-snippets-and-surround-with-snippets"></a>Fragmentos de código de expansión y fragmentos de código envolventes

En Visual Studio hay dos tipos de fragmento de código: los fragmentos de código de expansión, que se agregan en un punto de inserción especificado y se pueden reemplazar por un método abreviado de fragmento de código, y los fragmentos de código rodear con (solo en C# y C++), que se agregan alrededor de un bloque de código seleccionado.

Un ejemplo de un fragmento de código de expansión: en C# se utiliza el método abreviado tryf para insertar un bloque try-finally:

```csharp
try
{

}
finally
{

}
```

Para insertar este fragmento de código, haga clic en **Insertar fragmento de código** en el menú contextual de la ventana de código y, después, en **Visual C#**, escriba `tryf` y presione la tecla **TAB**. También puede escribir `tryf` y presionar **TAB** dos veces.

Un ejemplo de un fragmento de código rodear con: en el acceso directo de C++ `if` se puede utilizar como un fragmento de código de inserción o como un fragmento de código rodear con. Si selecciona una línea de código (por ejemplo, `return FALSE;`) y, después, hace clic en **Envolver con** > **if**, el fragmento de código se expandirá alrededor de la línea:

```cpp
if (true)
{
    return FALSE;
}
```

## <a name="snippet-replacement-parameters"></a>Parámetros de reemplazo de fragmentos de código

Los fragmentos de código pueden contener parámetros de reemplazo, que son marcadores de posición que debe reemplazar para incluir el código exacto que está escribiendo. En el ejemplo anterior `true` es un parámetro de reemplazo, que podría reemplazar por la condición adecuada. El reemplazo que haga se repetirá por cada instancia del mismo parámetro de reemplazo del fragmento de código.

Por ejemplo, en Visual Basic hay un fragmento de código que inserta una propiedad. Para insertar el fragmento de código, elija **Fragmento de código** > **Insertar fragmento de código** en el menú contextual en un archivo de código de Visual Basic. Luego, elija **Patrones de código** > **Propiedades, procedimientos, eventos** > **Definir una propiedad**.

![Opción Definir una propiedad del menú Fragmento de código](media/code-snippets-vb-property.png)

Se inserta el siguiente código:

```vb
Private newPropertyValue As String
Public Property NewProperty() As String
    Get
        Return newPropertyValue
    End Get
    Set(ByVal value As String)
        newPropertyValue = value
    End Set
End Property
```

Si cambia `newPropertyValue` por `m_property`, se cambian todas las instancias de `newPropertyValue`. Si cambia `String` por `Int` en la declaración de la propiedad, también se cambia a `Int` el valor en el método set.

## <a name="see-also"></a>Vea también

- [Tutorial: Crear un fragmento de código](../ide/walkthrough-creating-a-code-snippet.md)
- [Cómo: Distribuir fragmentos de código](../ide/how-to-distribute-code-snippets.md)
- [Procedimientos recomendados para usar fragmentos de código](../ide/best-practices-for-using-code-snippets.md)
- [Solucionar problemas con fragmentos de código](../ide/troubleshooting-snippets.md)
- [Fragmentos de código de C#](../ide/visual-csharp-code-snippets.md)
- [Fragmentos de código de Visual C++](../ide/visual-cpp-code-snippets.md)
- [Referencia de esquemas de fragmentos de código](../ide/code-snippets-schema-reference.md)
- [Fragmentos de código (Visual Studio para Mac)](/visualstudio/mac/snippets)