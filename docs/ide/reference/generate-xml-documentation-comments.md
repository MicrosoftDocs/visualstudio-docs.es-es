---
title: Inserción de comentarios de documentación XML en Visual Studio
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: e3c38e46a5c73d1f8018f56f76b971939ba8c316
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-insert-xml-comments-for-documentation-generation"></a>Cómo insertar comentarios XML para la generación de documentación

Visual Studio ayuda a documentar elementos de código (como las clases y los métodos) generando automáticamente la estructura de comentarios de documentación XML estándar. En tiempo de compilación, puede generar un archivo XML que contenga los comentarios de documentación. El archivo XML generado por el compilador se puede distribuir junto con el ensamblado .NET, de modo que Visual Studio y otros IDE puedan usar IntelliSense para mostrar información rápida sobre los tipos y los miembros. Además, el archivo XML se puede ejecutar mediante herramientas como [DocFX](https://dotnet.github.io/docfx/) y [Sandcastle](https://www.microsoft.com/download/details.aspx?id=10526) para generar sitios web de referencia de API.

> [!NOTE]
> El comando **Insertar comentario**, que inserta automáticamente comentarios de documentación XML, está disponible en [C#](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments) y [Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation), pero, aparte de esto, puede insertar manualmente [comentarios de documentación XML en archivos de C++](/cpp/ide/xml-documentation-visual-cpp) y seguir generando archivos de documentación XML en tiempo de compilación.

## <a name="to-insert-xml-comments-for-a-code-element"></a>Para insertar comentarios XML sobre un elemento de código

1. Coloque el cursor de texto sobre el elemento que desea documentar; por ejemplo, un método.

1. Realice una de las siguientes acciones:

   - Escriba `///` en C# o `'''` en Visual Basic.

   - En el menú **Edición**, elija **IntelliSense** > **Insertar comentario**.

   - En el menú contextual o justo encima del elemento de código, elija **Fragmento de código** > **Insertar comentario**.

   La plantilla XML se genera inmediatamente encima del elemento de código. Por ejemplo, al comentar un método, genera el elemento **\<summary\>**, un elemento **\<param\>** para cada parámetro y un elemento **\<returns\>** para documentar el valor devuelto.

   ![Plantilla de comentario XML (C#)](media/doc-preview-cs.png)

   ![Plantilla de comentario XML (Visual Basic)](media/doc-preview-vb.png)

1. Escriba una descripción de cada elemento XML para que esté completamente documentado.

   ![Comentario completado](media/doc-result-cs.png)

> [!NOTE]
> Hay un [opción](../../ide/reference/options-text-editor-csharp-advanced.md) para alternar los comentarios de documentación XML después de escribir `///` en C# o `'''` en Visual Basic. En la barra de menús, elija **Herramientas** > **Opciones** para abrir el cuadro de diálogo **Opciones**. Luego, vaya a **Editor de texto** > **C#** o **Basic** > **Avanzado**. En la sección **Ayuda del editor**, busque la opción **Generar comentarios de documentación XML**.

## <a name="see-also"></a>Vea también

- [Comentarios de documentación XML (Guía de programación de C#)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [Documentar el código con comentarios XML (Guía de C#)](/dotnet/csharp/codedoc)
- [Cómo: Crear documentación XML en Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)
- [Comentarios en C++](/cpp/cpp/comments-cpp)
- [Documentación XML (C++)](/cpp/ide/xml-documentation-visual-cpp)
- [Generación de código](../code-generation-in-visual-studio.md)