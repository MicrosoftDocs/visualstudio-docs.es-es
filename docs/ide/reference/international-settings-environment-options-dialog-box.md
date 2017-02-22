---
title: "Configuraci&#243;n internacional, Entorno, Opciones (Cuadro de di&#225;logo) | Microsoft Docs"
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
  - "VS.ToolsOptionsPages.Environment.InternationalSettings"
  - "VS.ToolsOptionsPages.Environment.International_Settings"
  - "VS.Environment.International Settings"
  - "VS.ToolsOptionsPag.Environment.International_Settings"
helpviewer_keywords: 
  - "Configuración internacional (cuadro de diálogo)"
  - "lenguajes, configuración del entorno"
  - "Cuadro de diálogo Opciones, configuración internacional"
  - "lenguajes, especificar predeterminados"
ms.assetid: e3a8815c-6995-4099-8e88-34f91fad55b2
caps.latest.revision: 14
caps.handback.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Configuraci&#243;n internacional, Entorno, Opciones (Cuadro de di&#225;logo)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La página Configuración internacional le permite cambiar el idioma predeterminado si tiene más de una versión de idioma del entorno de desarrollo integrado \(IDE\) instalado en su equipo.  Puede acceder a este cuadro de diálogo seleccionando **Opciones**desde el menú **Herramientas** y, a continuación, eligiendo **Configuración internacional** desde la carpeta **Entorno**.  Si esta página no aparece en la lista, en el cuadro dé diálogo **Opciones**, seleccione **Mostrar todas las configuraciones**.  
  
> [!NOTE]
>  Las opciones disponibles en los cuadros de diálogo, así como los nombres y las ubicaciones de los comandos de menú que se ven, podrían diferir de lo que se describe en la Ayuda, en función de los valores de configuración o de edición activos.  Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas**.  Para obtener más información, consulte [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 **Idioma**  
 Muestra los idiomas disponibles para las versiones de idioma del producto instalado.  Esta opción no está disponible a menos que tenga más de una versión de idioma instalada en su equipo.  Si varios idiomas de productos o una instalación de idiomas mixta de productos comparten el entorno, la selección del idioma se cambia a **Igual que en Microsoft Windows**.  
  
> [!CAUTION]
>  En un sistema con múltiples idiomas instalados, las herramientas de compilación de Visual C\+\+ \(cl.exe, link.exe, nmake.exe, bscmake.exe y archivos relacionados\) no se ven afectadas por esta configuración.  Estas herramientas usan la versión del último idioma instalado y las herramientas para el idioma instalado previamente se sobrescriben porque las herramientas de compilación de Visual C\+\+ no utilizan el modelo de archivo DLL satélite.  
  
## Vea también  
 [Instalar varias versiones de idioma de Visual Studio](../Topic/Installing%20Multiple%20Language%20Versions%20of%20Visual%20Studio.md)   
 [Opciones de entorno \(Cuadro de diálogo\)](../../ide/reference/environment-options-dialog-box.md)