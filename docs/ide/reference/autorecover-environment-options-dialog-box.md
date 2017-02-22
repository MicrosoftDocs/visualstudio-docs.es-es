---
title: "Autorrecuperaci&#243;n, Entorno, Opciones (Cuadro de di&#225;logo) | Microsoft Docs"
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
  - "VS.ToolsOptionsPag.Environment.AutoRecover"
  - "VS.DialogAutoRestore"
  - "VS.ToolsOptionsPages.Environment.AutoRecover"
  - "VS.ToolsOptionsPages.Environment.Auto_Save_and_Restore"
helpviewer_keywords: 
  - "archivos, recuperar"
  - "AutoRecover (página)"
  - "guardar archivos, automáticamente"
  - "archivos, guardar automáticamente"
ms.assetid: 397e5e44-4bbe-4289-94d1-642b466c9111
caps.latest.revision: 14
caps.handback.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Autorrecuperaci&#243;n, Entorno, Opciones (Cuadro de di&#225;logo)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Utilice esta página del cuadro de diálogo Opciones para especificar si se hará copia de seguridad de los archivos automáticamente o no.  Esta página también le permite especificar si se restaurarán o no los archivos modificados cuando el entorno de desarrollo integrado \(IDE\) se cierre inesperadamente.  Puede tener acceso a este cuadro de diálogo si selecciona el menú **Herramientas**, elige **Opciones**, selecciona la carpeta **Entorno** y elige la página **Autorrecuperación**.  Si esta página no aparece en la lista, seleccione **Mostrar todas las configuraciones** en el cuadro de diálogo **Opciones**.  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos.  Para cambiar su configuración, elija Importar y exportar configuraciones en el menú Herramientas.  Para obtener más información, vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 **Guardar información de Autorrecuperación cada \<n\> minutos**  
 Utilice esta opción para personalizar la frecuencia con la que se guarda automáticamente un archivo en el editor.  En el caso de los archivos guardados previamente, se guarda una copia del archivo en  \\...\\Mis documentos\\Visual Studio \<*versión*\>\\Backup Files\\\<*nombreDelProyecto*\>.  Si el archivo es nuevo y no se ha guardado manualmente, se guardará automáticamente con un nombre de archivo generado aleatoriamente.  
  
 **Guardar información de Autorrecuperación durante \<n\> días**  
 Utilice esta opción para especificar cuánto tiempo conserva Visual Studio los archivos creados para la autorrecuperación.  
  
## Vea también  
 [Opciones \(Cuadro de diálogo\)](../../ide/reference/options-dialog-box-visual-studio.md)