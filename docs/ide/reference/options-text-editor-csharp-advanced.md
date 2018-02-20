---
title: Opciones, editor de texto, C#, avanzado | Microsoft Docs
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced
helpviewer_keywords:
- XML comments
- XML documentation, generating
- outlining options [C#]
- XML documentation, creating
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 5d6cf8b655151e9b07111b6ac6fd64b6ad3c845f
ms.sourcegitcommit: 238cd48787391aa0ed1eb684f3f04e80f7958705
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2018
---
# <a name="options-text-editor-c-advanced"></a>Opciones, editor de texto, C#, avanzado

Use la página de opciones **Avanzado** para modificar la configuración del formato del editor, la refactorización de código y los comentarios de documentación XML para C#. Para obtener acceso a esta página de opciones, elija **Herramientas** > **Opciones** y, después, elija **Editor de texto** > **C#** > **Avanzado**.

> [!NOTE]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para más información, vea [Personalizar el IDE de Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="analysis"></a>Análisis

- Habilitar análisis de la solución completa

   Habilita el análisis de código en todos los archivos de la solución, no solo en los archivos de código abiertos. Para más información, vea [Full solution analysis](../../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md) (Análisis de la solución completa).

- Realizar el análisis de _características del editor en proceso externo (experimental)

## <a name="using-directives"></a>Directivas using

- Aplicar primero directivas "System" al ordenar instrucciones Using

- Separar grupos de directivas using

- Sugerir usos para tipos de ensamblados de referencia

- Sugerir usos para tipos de paquetes NuGet

## <a name="highlighting"></a>Resaltado

- Resaltar referencias al símbolo bajo el cursor

   Cuando el cursor esté colocado dentro de un símbolo, o cuando haga clic en un símbolo, todas las instancias de ese símbolo en el archivo de código se resaltan.

- Resaltar palabras clave relacionadas bajo el cursor

## <a name="outlining"></a>esquematizar

- Especificar el modo de esquematización al abrir los archivos

   Cuando está seleccionada, esquematiza automáticamente el archivo de código, lo que crea bloques contraíbles de código. La primera vez que se abre un archivo, los bloques #regions y los bloques de código inactivos se contraen.

- Mostrar separadores de línea de procedimientos

- Mostrar esquematización para construcciones a nivel de declaración

- Mostrar esquematización para construcciones a nivel de código

- Mostrar esquematización para regiones de preprocesador y comentarios

- Contraer #regions cuando se contraiga a las definiciones

## <a name="fading"></a>Corrección selectiva

- Atenuar directivas using no usadas

- Atenuar código inaccesible

## <a name="block-structure-guides"></a>Guías de estructura de bloque

- Mostrar guías para construcciones a nivel de declaración

- Mostrar guías para construcciones a nivel de código

## <a name="editor-help"></a>Ayuda del editor

- Generar comentarios de documentación XML para ///

   Cuando se selecciona, inserta los elementos XML de los comentarios de documentación XML después de escribir la introducción de comentario `///`. Para más información sobre la documentación XML, vea [Comentarios de documentación XML (Guía de programación de C#)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments).

- Insertar \* al comienzo de nuevas líneas al escribir comentarios /\* \*/

- Mostrar vista previa para seguimiento de cambio de nombre

- Dividir literales de cadena al presionar Entrar

- Informar sobre marcadores de posición no válidos en llamadas a "string.Format"

## <a name="extract-method"></a>Extraer método

- No colocar "out" o "ref" en estructura personalizada

## <a name="implement-interface-or-abstract-class"></a>Implementar interfaz o clase abstracta

- Al insertar propiedades, eventos y métodos, colóquelos: con otros miembros de la misma clase o al final

- Al generar propiedades: preferir propiedades de lanzamiento o preferir propiedades automáticas

## <a name="see-also"></a>Vea también

[Cómo insertar comentarios XML para la generación de documentación](../../ide/reference/generate-xml-documentation-comments.md)  
[Comentarios de documentación XML (Guía de programación de C#)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)  
[Documentar el código con comentarios XML (Guía de C#)](/dotnet/csharp/codedoc)  
[Opciones del editor específicas del lenguaje](../../ide/reference/setting-language-specific-editor-options.md)  
[IntelliSense para C#](../../ide/visual-csharp-intellisense.md)