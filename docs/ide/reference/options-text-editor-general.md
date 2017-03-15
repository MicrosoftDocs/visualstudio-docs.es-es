---
title: "Opciones, editor de texto, general | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.TOOLSOPTIONSPAGES.TEXT_EDITOR.SQL_SERVER_TOOLS.GENERAL"
  - "VS.ToolsOptionsPages.Text_Editor.All_Languages.General"
  - "VS.ToolsOptionsPages.Text_Editor.RDL_Expression.General"
  - "VS.ToolsOptionsPages.Text_Editor.SQL.General"
  - "vs.toolsoptionspages.text_editor"
  - "VS.ToolsOptionsPages.Text_Editor.XML.General"
  - "VS.ToolsOptionsPages.Text_Editor.T-SQL80.General"
  - "VS.ToolsOptionsPages.Text_Editor.CSS"
  - "VS.ToolsOptionsPages.Text_Editor.Plain_Text.General"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.General"
  - "VS.ToolsOptionsPages.Text_Editor.SQL_Script.General"
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.General"
  - "VS.ToolsOptionsPages.Text_Editor.All_Languages"
  - "VS.ToolsOptionsPages.Text_Editor.T-SQL7.General"
  - "VS.ToolsOptionsPages.Text_Editor.Basic.General"
  - "VS.ToolsOptionsPages.Text_Editor.T-SQL.General"
  - "vs.toolsoptionspages.text_editor.visual_jsharp"
  - "VS.ToolsOptionsPages.Text_Editor.F#.Tabs"
  - "VS.ToolsOptionsPages.Text_Editor.F#"
  - "VS.ToolsOptionsPages.Text_Editor.PL/SQL.General"
  - "VS.ToolsOptionsPages.Text_Editor.C/C++.General"
  - "VS.ToolsOptionsPages.Text_Editor.Plain_Text"
  - "VS.ToolsOptionsPages.Text_Editor.HTML"
  - "VS.ToolsOptionsPages.Text_Editor.XAML.General"
  - "VS.ToolsOptionsPages.Text_Editor"
  - "VS.ToolsOptionsPages.Text_Editor.F#.General"
  - "VS.ToolsOptionsPages.Text_Editor.XOML.General"
  - "VS.ToolsOptionsPages.Text_Editor.SQL"
  - "vs.toolsoptionspages.text_editor.c/c++"
  - "VS.ToolsOptionsPages.Text_Editor.SQL_Script"
  - "VS.ToolsOptionsPages.Text_Editor.T-SQL90.General"
  - "VS.ToolsOptionsPages.Text_Editor.General"
  - "VS.ToolsOptionsPages.Text_Editor.CSharp"
helpviewer_keywords: 
  - "Editor de texto, Opciones (cuadro de diálogo)"
  - "Editor de código"
  - "editor de texto [Visual Studio]"
  - "editores, configuración global"
ms.assetid: 4ac21e48-3243-4141-9058-7eaf12b3cde7
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# Opciones, editor de texto, general
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Con este cuadro de diálogo, se puede cambiar la configuración global del Editor de código y texto de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Para mostrar este cuadro de diálogo, haga clic en **Opciones** en el menú **Herramientas**, expanda la carpeta **Editor de texto** y, a continuación, haga clic en **General**.  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos.  Para cambiar la configuración, elija **Importar y exportar configuraciones** en el menú **Herramientas**.  Para obtener más información, vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Valores  
 Editar texto con arrastrar y colocar  
 Cuando está seleccionada, se puede mover texto seleccionándolo y arrastrándolo con el mouse a otra ubicación del documento actual o de otro documento abierto.  
  
 Resaltar con el delimitador automático  
 Cuando está seleccionada, se resaltan los caracteres delimitadores que separan los parámetros o los pares de elemento y valor, así como las llaves.  
  
 Control de cambios  
 Cuando se selecciona el editor de código, una línea amarilla vertical aparece en el margen de selección para marcar el código que han cambiado desde que se guardó por última vez.  Al guardar los cambios, las líneas verticales quedan verde.  
  
 Detectar automáticamente codificación UTF\-8 sin firma  
 De manera predeterminada, el editor detecta la codificación buscando marcas de orden de bytes o etiquetas de juegos de caracteres.  Si no encuentra ninguna en el documento actual, el editor de código intentará detectar automáticamente la codificación UTF\-8 mediante el examen de las secuencias de bytes.  Para deshabilitar la detección automática de la codificación, desactive esta opción.  
  
## Display  
 Margen de la selección  
 Cuando está seleccionada, aparece un margen vertical junto al borde izquierdo del área de texto del editor.  Se puede hacer clic en este margen para seleccionar una línea de texto completa o hacer clic y arrastrar para seleccionar líneas de texto consecutivas.  
  
|Margen de la selección activado|Margen de la selección desactivado|  
|-------------------------------------|----------------------------------------|  
|![Captura de pantalla de HTMLpageSelectionMarginOn](../../ide/reference/media/vxselmaron.png "vxSelmaron")|![Captura de pantalla de HTMLpageSelectionMarginOff](../../ide/reference/media/vxselmaroff.gif "vxSelmaroff")|  
  
 Margen del indicador  
 Cuando está seleccionada, aparece un margen vertical fuera del borde izquierdo del área de texto del editor.  Al hacer clic en este margen, se muestra un icono e información sobre herramientas relacionados con el texto.  Por ejemplo, en el margen del indicador aparecen accesos directos a un punto de interrupción o a la lista de tareas.  Esta información no se imprime.  
  
 Barra de desplazamiento vertical  
 Al seleccionar esta opción, aparece una barra de desplazamiento vertical que permite desplazarse hacia arriba o hacia abajo para ver elementos que quedan fuera del área visible del Editor.  Si no hay ninguna barra de desplazamiento vertical disponible, pueden utilizarse las teclas RePág, AvPág y las teclas de dirección para desplazarse.  
  
 Barra de desplazamiento horizontal  
 Al seleccionar esta opción, aparece una barra de desplazamiento horizontal que permite desplazarse de un lado a otro para ver elementos que quedan fuera del área visible del Editor.  Si no hay ninguna barra de desplazamiento horizontal disponible, pueden utilizarse las teclas de dirección para desplazarse.  
  
 Línea actual resaltada  
 Cuando se activa, muestra un cuadro gris alrededor de la línea de código en la que el cursor se encuentra.  
  
## Vea también  
 [Opciones, Editor de texto, Todos los lenguajes](../../ide/reference/options-text-editor-all-languages.md)   
 [Opciones, editor de texto, todos los lenguajes, pestañas](../../ide/reference/options-text-editor-all-languages-tabs.md)   
 [Opciones, editor de texto, extensión de archivo](../../ide/reference/options-text-editor-file-extension.md)   
 [Identificar y personalizar métodos abreviados de teclado](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)   
 [Personalizar el editor](../../ide/customizing-the-editor.md)   
 [Utilizar IntelliSense](../../ide/using-intellisense.md)