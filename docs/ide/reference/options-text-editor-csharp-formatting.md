---
title: "Opciones, editor de texto, C#, formato | Microsoft Docs"
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
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Spacing"
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.NewLines"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.General"
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Indentation"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.NewLines"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Indentation"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Wrapping"
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Wrapping"
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting"
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.General"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Spacing"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting"
helpviewer_keywords: 
  - "aplicar formato [C#]"
  - "aplicar formato [J#]"
  - "Cuadro de diálogo Opciones del Editor de texto, formato"
ms.assetid: 5a7bb668-1d0c-4ffe-9508-24592813162e
caps.latest.revision: 23
caps.handback.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Opciones, editor de texto, C#, formato
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

El cuadro de diálogo de página de propiedades **Formato** se utiliza para establecer las opciones de formato del código en el Editor de código.  Para tener acceso a este cuadro de diálogo, haga clic en **Opciones** en el menú **Herramientas**, expanda **Editor de texto**, expanda **C\#**y, a continuación, haga clic en **Formato**.  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos.  Para cambiar la configuración, elija **Importar y exportar configuraciones** en el menú **Herramientas**.  Para obtener más información, vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Configuración general  
 La configuración general afecta a cómo el Editor de código aplica las opciones de formato al código.  
  
## Lista de UIElement  
  
|Etiqueta|Descripción|  
|--------------|-----------------|  
|**Formato completado automáticamente de la instrucción ;**|Cuando está activada, da formato al acabar a las instrucciones de acuerdo con las opciones de formato seleccionadas para el Editor de código.  Desactive esta casilla si no desea que el Editor de código modifique las instrucciones.|  
|**Formato completado automáticamente del bloque }**|Cuando está activada, da formato a los bloques de código tan pronto como éstos finalizan, de acuerdo con las opciones de formato seleccionadas para el Editor de código.  Desactive esta casilla si no desea que el Editor de código modifique los bloques.|  
|**Ajustar sangría al pegar**|Cuando está activada, da formato a texto pegado en el Editor de código de forma que se ajuste a las opciones de formato seleccionadas para el Editor de código.  Desactive esta casilla si no desea modificar el texto pegado.|  
  
## Vista previa \(ventana\)  
 Los paneles **Sangría**, **Nuevas líneas**, **Espaciado** y **Ajuste** presentan una ventana de vista previa.  La ventana de vista previa muestra el efecto de cada opción.  Para utilizar la ventana de vista previa, seleccione una opción de formato.  La ventana de vista previa muestra un ejemplo de la opción seleccionada.  Cuando modifica los valores, por ejemplo, al activar o desactivar una casilla para modificar la configuración, se actualiza la ventana de vista previa para mostrar el efecto de esta nueva configuración.  
  
## Comentarios  
 Las opciones de sangría de las páginas **Tabulaciones** de cada idioma determinan únicamente dónde se situará el cursor en el Editor de código cuando se presione ENTRAR al final de una línea.  Las opciones de sangría de **Formato** se aplican cuando se aplica el formato al código automáticamente, por ejemplo, cuando se pega el código en el archivo con la opción **Ajustar sangría al pegar** activada, y también cuando se escribe manualmente el bloque al que se aplica el formato.  
  
## Vea también  
 [General, Entorno, Opciones \(Cuadro de diálogo\)](../../ide/reference/general-environment-options-dialog-box.md)