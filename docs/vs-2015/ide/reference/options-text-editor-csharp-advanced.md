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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4f2d11e78c2402a6541bc87748ed6ba348ba80fc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662317"
---
# <a name="options-text-editor-c-advanced"></a>Opciones, editor de texto, C#, avanzado
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Use este cuadro de diálogo para modificar la configuración del formato del editor, la refactorización de código y los comentarios de documentación XML para Visual C#. Para tener acceso a este cuadro de diálogo, haga clic en **Opciones** en el menú **Herramientas**, expanda la carpeta **Editor de texto**, expanda **C#** y, después, haga clic en **Opciones avanzadas**.

> [!NOTE]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="outlining"></a>esquematizar
 Especificar el modo de esquematización al abrir los archivos cuando se selecciona, describe automáticamente el archivo de código, que crea bloques de código contraíbles. La primera vez que se abre un archivo, los bloques #regions y los bloques de código inactivos se contraen.

## <a name="editor-help"></a>Ayuda del editor
 Los errores de subrayado en el editor identifican los errores de compilación en el código. Cuando esta opción está seleccionada, aparecen subrayados ondulados de colores que tienen significados específicos:

- Los errores de análisis son rojos.

- Los errores de compilación son azules.

- Las advertencias de compilación son verdes.

- Las ediciones [Editar y continuar](../../debugger/edit-and-continue.md) no válidas son moradas.

  Mueva el puntero sobre el segmento de código subrayado para ver información sobre herramientas con información sobre el error.

  Mostrar errores semánticos en vivo identifica determinados errores de compilación sin compilación explícita, por ejemplo, declarar y usar un tipo desconocido o hacer referencia a una propiedad desconocida.

  Resaltar referencias al símbolo en cursor cuando el cursor se coloca dentro de un símbolo, o al hacer clic en un símbolo, se resaltan todas las instancias de ese símbolo en el archivo de código.

## <a name="refactoring"></a>Refactorización
 Comprobar los resultados de la refactorización muestra el cuadro de diálogo resultados de la **comprobación** cuando se intenta refactorizar código que contiene errores de compilación o cuando la refactorización haría que una referencia de código se enlazara a algo diferente de su enlace original.

 Advertir en miembros con referencias generadas por el compilador muestra un cuadro de diálogo de advertencia al intentar refactorizar un miembro que tiene el mismo nombre que una referencia generada por el compilador.

## <a name="xml-documentation-comments"></a>Comentarios de la documentación XML
 Generar comentarios de documentación XML para///si se selecciona, inserta el \<summary > Etiquetas de inicio y finalización automáticamente para los comentarios de documentación XML después de escribir la introducción a///comentario. Para obtener más información sobre la documentación XML, vea [Comentarios de documentación XML](https://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199).

## <a name="implement-interface"></a>Implementar interfaz
 El código generado envolvente con #region inserta un #region \<*nombre*de la interfaz > en torno a los métodos cuando se utiliza la instrucción implementar interfaz o implementar interfaz explícitamente.

## <a name="organize-usings"></a>Organizar instrucciones Using
 Coloque primero las directivas ' System ' al ordenar Using cuando se selecciona, `System` las directivas Using aparecen antes que otras directivas using. Para más información, vea [Organización de directivas using](../../misc/sort-usings.md).

## <a name="see-also"></a>Otras referencias
 [Comentarios de documentación XML](https://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199) [establecer opciones del editor específicas del lenguaje](../../ide/reference/setting-language-specific-editor-options.md) [Visual C# IntelliSense](../../ide/visual-csharp-intellisense.md)
