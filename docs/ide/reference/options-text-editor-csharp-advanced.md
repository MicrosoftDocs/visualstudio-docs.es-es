---
title: Opciones, editor de texto, C#, avanzado
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: ab08de0c6993f57c719f69ccf27e30e3cbe41c32
ms.sourcegitcommit: 80f9daba96ff76ad7e228eb8716df3abfd115bc3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2018
ms.locfileid: "37433307"
---
# <a name="options-text-editor-c-advanced"></a>Opciones, editor de texto, C#, avanzado

Use la página de opciones **Avanzado** para modificar la configuración del formato del editor, la refactorización de código y los comentarios de documentación XML para C#. Para obtener acceso a esta página de opciones, elija **Herramientas** > **Opciones** y, después, elija **Editor de texto** > **C#** > **Avanzado**.

> [!NOTE]
> Puede ser que aquí no aparezcan todas las opciones.

## <a name="analysis"></a>Análisis

- Habilitar análisis de la solución completa

   Habilita el análisis de código en todos los archivos de la solución, no solo en los archivos de código abiertos. Para más información, vea [Full solution analysis](../../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md) (Análisis de la solución completa).

## <a name="highlighting"></a>Resaltado

- Resaltar referencias al símbolo bajo el cursor

   Cuando el cursor esté colocado dentro de un símbolo, o cuando haga clic en un símbolo, todas las instancias de ese símbolo en el archivo de código se resaltan.

## <a name="outlining"></a>esquematizar

- Especificar el modo de esquematización al abrir los archivos

   Cuando está seleccionada, esquematiza automáticamente el archivo de código, lo que crea bloques contraíbles de código. La primera vez que se abre un archivo, los bloques #regions y los bloques de código inactivos se contraen.

## <a name="editor-help"></a>Ayuda del editor

- Generar comentarios de documentación XML para ///

   Cuando se selecciona, inserta los elementos XML de los comentarios de documentación XML después de escribir la introducción de comentario `///`. Para más información sobre la documentación XML, vea [Comentarios de documentación XML (Guía de programación de C#)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments).

## <a name="see-also"></a>Vea también

- [Cómo insertar comentarios XML para la generación de documentación](../../ide/reference/generate-xml-documentation-comments.md)
- [Comentarios de documentación XML (Guía de programación de C#)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [Documentar el código con comentarios XML (Guía de C#)](/dotnet/csharp/codedoc)
- [Opciones del editor específicas del lenguaje](../../ide/reference/setting-language-specific-editor-options.md)
- [IntelliSense para C#](../../ide/visual-csharp-intellisense.md)