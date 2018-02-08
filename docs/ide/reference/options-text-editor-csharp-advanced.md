---
title: Opciones, editor de texto, C#, avanzado | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Advanced
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced
helpviewer_keywords:
- XML comments
- XML documentation, generating
- outlining options [C#]
- XML documentation, creating
ms.assetid: 947f9d9a-b0f3-408d-9866-d82895bcee31
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 193b61ab95daa84c5815c251c7d52103c88977e1
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2018
---
# <a name="options-text-editor-c-advanced"></a>Opciones, editor de texto, C#, avanzado
Use este cuadro de diálogo para modificar la configuración del formato del editor, la refactorización de código y los comentarios de documentación XML para C#. Para tener acceso a este cuadro de diálogo, haga clic en **Opciones** en el menú **Herramientas**, expanda la carpeta **Editor de texto**, expanda **C#** y, después, haga clic en **Opciones avanzadas**.  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para más información, vea [Personalizar el IDE de Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="outlining"></a>esquematizar  
 Especificar el modo de esquematización al abrir los archivos  
 Cuando está seleccionada, esquematiza automáticamente el archivo de código, lo que crea bloques contraíbles de código. La primera vez que se abre un archivo, los bloques #regions y los bloques de código inactivos se contraen.  
  
## <a name="editor-help"></a>Ayuda del editor  
 Subrayar errores en el editor  
 Identifica errores de compilación en el código. Cuando esta opción está seleccionada, aparecen subrayados ondulados de colores que tienen significados específicos:  
  
-   Los errores de análisis son rojos.  
  
-   Los errores de compilación son azules.  
  
-   Las advertencias de compilación son verdes.  
  
-   Las ediciones [Editar y continuar](../../debugger/edit-and-continue.md) no válidas son moradas.  
  
Mueva el puntero sobre el segmento de código subrayado para ver información sobre herramientas con información sobre el error.  
  
Mostrar errores semánticos activos  
Identifica determinados errores de compilación sin una compilación explícita, por ejemplo, mediante la declaración y el uso de un tipo desconocido o haciendo referencia a una propiedad desconocida.  
  
Resaltar referencias al símbolo bajo el cursor  
Cuando el cursor esté colocado dentro de un símbolo, o cuando haga clic en un símbolo, todas las instancias de ese símbolo en el archivo de código se resaltan.  
  
## <a name="refactoring"></a>Refactorización  
 Comprobar resultados de refactorización  
 El cuadro de diálogo **Resultados de la comprobación** se muestra cuando intenta refactorizar código que contiene errores de compilación, o cuando la refactorización provocará que una referencia de código se enlace a algo diferente a su enlace original.  
  
 Advertir si hay miembros con referencias generadas por el compilador  
 Se muestra un cuadro de diálogo de advertencia cuando intenta refactorizar un miembro que tiene el mismo nombre que una referencia generada por el compilador.  
  
## <a name="xml-documentation-comments"></a>Comentarios de la documentación XML  
 Generar comentarios de documentación XML para ///  
 Cuando está seleccionada, inserta las etiquetas de inicio y final \<summary> automáticamente para los comentarios de documentación XML después de que escriba la introducción de comentario ///. Para obtener más información sobre la documentación XML, vea [Comentarios de documentación XML](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments).  
  
## <a name="implement-interface"></a>Implementar interfaz  
 Delimitar el código generado con #region  
 Inserta un miembro \<*nombre de interfaz*> #region alrededor de los métodos cuando se usa Implementar interfaz o Implementar interfaz explícitamente.  
  
## <a name="organize-usings"></a>Organizar instrucciones Using  
 Aplicar primero directivas "System" al ordenar instrucciones Using  
 Cuando está seleccionada, las directivas Using `System` aparecen antes que otras directivas Using. Para obtener más información, vea Organizar instrucciones Using en [IntelliSense para C#](../../ide/visual-csharp-intellisense.md#automatic-code-generation).  
  
## <a name="see-also"></a>Vea también  
 [Comentarios de documentación XML](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)   
 [Opciones del editor específicas del lenguaje](../../ide/reference/setting-language-specific-editor-options.md)   
 [IntelliSense para C#](../../ide/visual-csharp-intellisense.md)