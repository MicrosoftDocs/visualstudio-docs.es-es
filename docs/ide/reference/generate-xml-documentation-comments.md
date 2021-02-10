---
title: Inserción de comentarios de documentación XML
description: Obtenga información sobre cómo insertar comentarios de documentación XML en el código que puede usar para crear un archivo XML generado por el compilador para distribuirlo junto con el ensamblado .NET.
ms.custom: SEO-VS-2020
ms.date: 01/22/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 2c203d9a445d9426a8079801a856e20f7be82229
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946571"
---
# <a name="how-to-insert-xml-comments-for-documentation-generation"></a>Cómo insertar comentarios XML para la generación de documentación

Visual Studio ayuda a documentar elementos de código (como las clases y los métodos) generando automáticamente la estructura de comentarios de documentación XML estándar. En tiempo de compilación, puede generar un archivo XML que contenga los comentarios de documentación.

> [!TIP]
> Para información sobre cómo configurar el nombre y la ubicación del archivo XML generado, consulte [Documentar el código con comentarios XML (Guía de C#)](/dotnet/csharp/codedoc).

El archivo XML generado por el compilador se puede distribuir junto con el ensamblado .NET, de modo que Visual Studio y otros IDE puedan usar IntelliSense para mostrar información rápida sobre los tipos y los miembros. Además, el archivo XML se puede ejecutar mediante herramientas como [DocFX](https://dotnet.github.io/docfx/) y [Sandcastle](https://www.microsoft.com/download/details.aspx?id=10526) para generar sitios web de referencia de API.

> [!NOTE]
> El comando **Insertar comentario**, que inserta automáticamente comentarios de documentación XML, está disponible en [C#](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments) y [Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation), pero, aparte de esto, puede insertar manualmente [comentarios de documentación XML en archivos de C++](/cpp/build/reference/xml-documentation-visual-cpp) y seguir generando archivos de documentación XML en tiempo de compilación.

## <a name="to-insert-xml-comments-for-a-code-element"></a>Para insertar comentarios XML sobre un elemento de código

1. Coloque el cursor de texto sobre el elemento que desea documentar; por ejemplo, un método.

2. Realice una de las siguientes acciones:

   - Escriba `///` en C# o `'''` en Visual Basic.

   - En el menú **Edición**, elija **IntelliSense** > **Insertar comentario**.

   - En el menú contextual o justo encima del elemento de código, elija **Fragmento de código** > **Insertar comentario**.

   La plantilla XML se genera inmediatamente encima del elemento de código. Por ejemplo, al comentar un método, genera el elemento **\<summary\>** , un elemento **\<param\>** para cada parámetro y un elemento **\<returns\>** para documentar el valor devuelto.

   ![Plantilla de comentario XML (C#)](media/doc-preview-cs.png)

   ![Plantilla de comentario XML (Visual Basic)](media/doc-preview-vb.png)

3. Escriba una descripción de cada elemento XML para que esté completamente documentado.

   ![Captura de pantalla en la que se muestra el comentario completado.](media/doc-result-cs.png)

Puede usar estilos en comentarios XML que se representarán en Información rápida al mantener el mouse sobre el elemento. Estos estilos incluyen cursiva, negrita, viñetas y un vínculo interactivo.

   ![Captura de pantalla en la que se muestra el comentario completado con etiquetas de estilo para cursiva, negrita, viñetas y un vínculo en el que se hace clic.](media/doc-style-cs.png) 

> [!NOTE]
> Hay un [opción](../../ide/reference/options-text-editor-csharp-advanced.md) para alternar los comentarios de documentación XML después de escribir `///` en C# o `'''` en Visual Basic. En la barra de menús, elija **Herramientas** > **Opciones** para abrir el cuadro de diálogo **Opciones**. Luego, vaya a **Editor de texto** > **C#** o **Basic** > **Avanzado**. En la sección **Ayuda del editor**, busque la opción **Generar comentarios de documentación XML**.

## <a name="see-also"></a>Vea también

- [Comentarios de documentación XML (Guía de programación de C#)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [Documentar el código con comentarios XML (Guía de C#)](/dotnet/csharp/codedoc)
- [Cómo: Crear documentación XML en Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)
- [Comentarios en C++](/cpp/cpp/comments-cpp)
- [Documentación XML (C++)](/cpp/build/reference/xml-documentation-visual-cpp)
- [Generación de código](../code-generation-in-visual-studio.md)
