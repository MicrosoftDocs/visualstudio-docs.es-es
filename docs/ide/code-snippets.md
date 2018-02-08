---
title: "Fragmentos de código | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.ExpansionManagerImport
- vs.codesnippetmanager
helpviewer_keywords:
- code snippets, replacement parameters
- code snippets, surround with
- replacement parameters
- code snippets, expansion
- surround with
- code snippets
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 32aded825454ce53193d488c01e3aad70d9032f8
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2018
---
# <a name="code-snippets"></a>Fragmentos de código

Los fragmentos de código son pequeños bloques de código reutilizable que se pueden insertar en un archivo de código mediante un comando de menú contextual o una combinación de teclas de acceso rápido. Normalmente contienen bloques de código muy utilizados, como bloques try-finally o if-else, pero pueden utilizarse para insertar clases o métodos completos.

## <a name="expansion-snippets-and-surround-with-snippets"></a>Fragmentos de código de expansión y fragmentos de código Rodear con

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

Puede insertar este fragmento de código haciendo clic en **Insertar fragmento de código** en el menú contextual de la ventana de código y, después, en **Visual C#**. Tras ello, escriba `tryf` y presione la tecla **TAB**. También puede escribir `tryf` y presionar **TAB** dos veces.

Un ejemplo de un fragmento de código rodear con: en el acceso directo de C++ `if` se puede utilizar como un fragmento de código de inserción o como un fragmento de código rodear con. Si selecciona una línea de código (por ejemplo, `return FALSE;`) y, después, hace clic en **Rodear con** y en **si**, el fragmento de código se expande alrededor de la línea:

```cpp
if (true)
{
    return FALSE;
}
```

## <a name="snippet-replacement-parameters"></a>Parámetros de reemplazo de fragmentos de código

Los fragmentos de código pueden contener parámetros de reemplazo, que son marcadores de posición que debe reemplazar para incluir el código exacto que está escribiendo. En el ejemplo anterior `true` es un parámetro de reemplazo, que podría reemplazar por la condición adecuada. El reemplazo que haga se repetirá por cada instancia del mismo parámetro de reemplazo del fragmento de código.

Por ejemplo, en Visual Basic hay fragmento de código que inserta una propiedad. Haga clic en **Insertar fragmento de código** en el menú contextual de la ventana de código, en **Modelos de código**, **Propiedades, procedimientos, eventos** y, por último, en Definir una propiedad. Se inserta el siguiente código:

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

## <a name="code-snippet-manager"></a>Administrador de fragmentos de código

Puede ver todos los fragmentos de código instalados actualmente, además de su ubicación en el disco; para ello, haga clic en **Herramientas**, **Administrador de fragmentos de código**. Los fragmentos de código se ordenan por idioma.

Puede agregar y eliminar directorios de fragmentos de código con los botones **Agregar** y **Eliminar** del cuadro de diálogo **Administrador de fragmentos de código**. Para agregar fragmentos de código individuales, utilice el botón **Importar**.

## <a name="see-also"></a>Vea también

[Tutorial: Crear un fragmento de código](../ide/walkthrough-creating-a-code-snippet.md)  
[Cómo: Distribuir fragmentos de código](../ide/how-to-distribute-code-snippets.md)  
[Procedimientos recomendados para usar fragmentos de código](../ide/best-practices-for-using-code-snippets.md)  
[Solucionar problemas con fragmentos de código](../ide/troubleshooting-snippets.md)  
[Fragmentos de código de C#](../ide/visual-csharp-code-snippets.md)  
[Fragmentos de código de Visual C++](../ide/visual-cpp-code-snippets.md)  
[Referencia de esquemas de fragmentos de código](../ide/code-snippets-schema-reference.md)