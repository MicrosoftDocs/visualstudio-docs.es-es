---
title: Fragmentos de código | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
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
ms.assetid: 85976ad9-4c9a-4e7b-896e-66ec6f955199
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e28ebd46a03983e60ebdd3fc22dd55d85249f710
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68188857"
---
# <a name="code-snippets"></a>Fragmentos de código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los fragmentos de código son pequeños bloques de código reutilizable que se pueden insertar en un archivo de código mediante un comando de menú contextual o una combinación de teclas de acceso rápido. Normalmente contienen bloques de código muy utilizados, como bloques try-finally o if-else, pero pueden utilizarse para insertar clases o métodos completos.  
  
## <a name="expansion-snippets-and-surround-with-snippets"></a>Fragmentos de código de expansión y fragmentos de código Rodear con  
 En Visual Studio hay dos tipos de fragmento de código: los fragmentos de código de expansión, que se agregan en un punto de inserción especificado y se pueden reemplazar por un método abreviado de fragmento de código, y los fragmentos de código rodear con (solo en C# y C++), que se agregan alrededor de un bloque de código seleccionado.  
  
 Un ejemplo de un fragmento de código de inserción: en C# se utiliza el método abreviado tryf para insertar un bloque try-finally:  
  
```  
try  
{  
  
}  
finally  
{  
  
}  
  
```  
  
 Puede insertar este fragmento de código haciendo clic en **Insertar fragmento de código** en el menú contextual de la ventana de código y, después, en **Visual C#** . A continuación, escriba `tryf` y pulse el tabulador. También puede escribir `tryf` y pulsar el tabulador dos veces seguidas.  
  
 Un ejemplo de un fragmento de código rodear con: en el acceso directo de C++ `if` se puede utilizar como un fragmento de código de inserción o como un fragmento de código rodear con. Si selecciona una línea de código (por ejemplo, `return FALSE;`) y, después, hace clic en **Rodear con** y en **si**, el fragmento de código se expande alrededor de la línea:  
  
```  
if (true)  
{  
    return FALSE;  
}  
  
```  
  
## <a name="snippet-replacement-parameters"></a>Parámetros de reemplazo de fragmentos de código  
 Los fragmentos de código pueden contener parámetros de reemplazo, que son marcadores de posición que debe reemplazar para incluir el código exacto que está escribiendo. En el ejemplo anterior `true` es un parámetro de reemplazo, que podría reemplazar por la condición adecuada. El reemplazo que haga se repetirá por cada instancia del mismo parámetro de reemplazo del fragmento de código.  
  
 Por ejemplo, en Visual Basic hay fragmento de código que inserta una propiedad. Haga clic en **Insertar fragmento de código** en el menú contextual de la ventana de código, en **Modelos de código**, **Propiedades, procedimientos, eventos** y, por último, en Definir una propiedad. Se inserta el siguiente código:  
  
```  
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
 Se pueden ver todos los fragmentos de código instalados actualmente, además de su ubicación en el disco, haciendo clic en **Herramientas/Administrador de fragmentos de código**. Los fragmentos de código se ordenan por idioma.  
  
 Puede agregar y eliminar directorios de fragmentos de código con los botones **Agregar** y **Eliminar** del cuadro de diálogo **Administrador de fragmentos de código**. Para agregar fragmentos de código individuales, utilice el botón **Importar**.  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: Creación de un fragmento de código](../ide/walkthrough-creating-a-code-snippet.md)   
 [Cómo: Distribuir fragmentos de código](../ide/how-to-distribute-code-snippets.md)   
 [Procedimientos recomendados para usar fragmentos de código](../ide/best-practices-for-using-code-snippets.md)   
 [Solucionar problemas con fragmentos de código](../ide/troubleshooting-snippets.md)   
 [Fragmentos de código de Visual C#](../ide/visual-csharp-code-snippets.md)   
 [Fragmentos de código de Visual C++](../ide/visual-cpp-code-snippets.md)   
 [Referencia de esquemas de fragmentos de código](../ide/code-snippets-schema-reference.md)
