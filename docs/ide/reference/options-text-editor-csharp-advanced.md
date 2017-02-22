---
title: "Opciones, editor de texto, C#, avanzado | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Advanced"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Outlining"
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced"
helpviewer_keywords: 
  - "comentarios XML"
  - "documentación XML, generar"
  - "opciones de esquematización [C#]"
  - "opciones de esquematización [J#]"
  - "documentación XML, crear"
ms.assetid: 947f9d9a-b0f3-408d-9866-d82895bcee31
caps.latest.revision: 22
caps.handback.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Opciones, editor de texto, C#, avanzado
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Utilice este cuadro de diálogo para modificar la configuración de la asignación de formato del editor, la refactorización de código y los comentarios de la documentación XML de Visual C\#.  Para tener acceso a este cuadro de diálogo, haga clic en **Opciones** en el menú **Herramientas**, expanda la carpeta **Editor de texto**, expanda **C\#**y, a continuación, haga clic en **Avanzadas**.  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos.  Para cambiar la configuración, elija **Importar y exportar configuraciones** en el menú **Herramientas**.  Para obtener más información, vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Esquematización  
 Especificar el modo de esquematización al abrir los archivos  
 Cuando se selecciona, esquematiza automáticamente el archivo de código, que crea bloques de código plegables.  La primera vez que se abre un archivo, se contraen los bloques \#region y los bloques de código inactivos.  
  
## Ayuda del editor  
 Subrayar errores en el editor  
 Identifica errores de compilación en el código.  Cuando se selecciona esta opción, los subrayados ondulados aparecen en colores que tienen significados concretos:  
  
-   Los errores de análisis son rojos.  
  
-   Los errores de compilación son azules.  
  
-   Las advertencias de compilación son verdes.  
  
-   Las ediciones [Editar y continuar](../../debugger/edit-and-continue.md) no válidas son de color púrpura.  
  
 Mueva el puntero sobre el segmento de código subrayado para ver información sobre herramientas acerca del error.  
  
 Mostrar errores semánticos activos  
 Identifica algunos errores de compilación sin compilación explícita, por ejemplo, declarar y utilizar un tipo desconocido o hacer referencia a una propiedad desconocida.  
  
 Resaltar referencias al símbolo bajo el cursor  
 Cuando el cursor se coloca dentro de un símbolo, o al hacer clic en un símbolo, todas las instancias de dicho símbolo en el archivo de código se resaltan.  
  
## Refactorización  
 Compruebe los resultados de la refactorización  
 Muestra el cuadro de diálogo **Resultados de la comprobación** cuando se intenta refactorizar código que contiene errores de compilación, o cuando la refactorización causa que una referencia de código se enlace a otro objeto distinto de su enlace original.  
  
 Advertir si hay miembros con referencias generadas por el compilador  
 Muestra un diálogo con la advertencia al intentar refactorizar un miembro que tiene el mismo nombre que una referencia generada por un compilador.  
  
## Comentarios de la documentación XML  
 Generar comentarios de documentación XML para \/\/\/  
 Cuando se selecciona, inserta automáticamente las etiquetas de inicio y cierre \<summary\> de los comentarios de documentación XML después de que se escriba la introducción del comentario \/\/\/.  Para obtener más información acerca de la documentación XML, vea [Comentarios de documentación XML](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments).  
  
## Implementar interfaz  
 Delimitar el código generado con \#region  
 Inserta un bloque \#region \<*nombreInterfaz*\> Miembro alrededor de los métodos cuando se utiliza la opción Implementar interfaz o Implementar interfaz explícitamente.  
  
## Organizar Usings  
 Aplicar primero directivas 'System' al ordenar usos  
 Cuando se selecciona, las directivas que utiliza `System` aparecen antes de otras directivas que se estén utilizando.  Para obtener más información, vea [Ordenar usos](../../misc/sort-usings.md).  
  
## Vea también  
 [Comentarios de documentación XML](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)   
 [Opciones del editor específicas del lenguaje](../../ide/reference/setting-language-specific-editor-options.md)   
 [IntelliSense para Visual C\#](../../ide/visual-csharp-intellisense.md)