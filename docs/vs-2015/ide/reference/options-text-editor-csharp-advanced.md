---
title: Opciones, editor de texto, C#, avanzado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Advanced
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced
helpviewer_keywords:
- XML comments
- XML documentation, generating
- outlining options [C#]
- outlining options [J#]
- XML documentation, creating
ms.assetid: 947f9d9a-b0f3-408d-9866-d82895bcee31
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ed1260d414c21d40bd0dc57f885cf5996594b7d6
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 04/17/2019
ms.locfileid: "59664558"
---
# <a name="options-text-editor-c-advanced"></a>Opciones, editor de texto, C#, avanzado
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Use este cuadro de diálogo para modificar la configuración del formato del editor, la refactorización de código y los comentarios de documentación XML para Visual C#. Para tener acceso a este cuadro de diálogo, haga clic en **Opciones** en el menú **Herramientas**, expanda la carpeta **Editor de texto**, expanda **C#** y, después, haga clic en **Opciones avanzadas**.  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="outlining"></a>esquematizar  
 Especificar el modo de esquematización al abrir los archivos  
 Cuando está seleccionada, esquematiza automáticamente el archivo de código, lo que crea bloques contraíbles de código. La primera vez que se abre un archivo, los bloques #regions y los bloques de código inactivos se contraen.  
  
## <a name="editor-help"></a>Ayuda del editor  
 Subrayar errores en el editor  
 Identifica errores de compilación en el código. Cuando esta opción está seleccionada, aparecen subrayados ondulados de colores que tienen significados específicos:  
  
- Los errores de análisis son rojos.  
  
- Los errores de compilación son azules.  
  
- Las advertencias de compilación son verdes.  
  
- Las ediciones [Editar y continuar](../../debugger/edit-and-continue.md) no válidas son moradas.  
  
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
 Cuando está seleccionada, inserta las etiquetas de inicio y final \<summary> automáticamente para los comentarios de documentación XML después de que escriba la introducción de comentario ///. Para obtener más información sobre la documentación XML, vea [Comentarios de documentación XML](http://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199).  
  
## <a name="implement-interface"></a>Implementar interfaz  
 Delimitar el código generado con #region  
 Inserta un miembro \<*nombre de interfaz*> #region alrededor de los métodos cuando se usa Implementar interfaz o Implementar interfaz explícitamente.  
  
## <a name="organize-usings"></a>Organizar instrucciones Using  
 Aplicar primero directivas "System" al ordenar instrucciones Using  
 Cuando está seleccionada, las directivas Using `System` aparecen antes que otras directivas Using. Para más información, vea [Organización de directivas using](../../misc/sort-usings.md).  
  
## <a name="see-also"></a>Vea también  
 [Comentarios de documentación XML](http://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199)   
 [Opciones del editor específicas del lenguaje](../../ide/reference/setting-language-specific-editor-options.md)   
 [IntelliSense para Visual C#](../../ide/visual-csharp-intellisense.md)
