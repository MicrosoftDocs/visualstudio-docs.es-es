---
title: "C&#243;mo: Especificar el binario de inicio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.property.itemlaunch"
helpviewer_keywords: 
  - "herramientas de generación de perfiles, iniciar"
  - "herramientas de rendimiento, iniciar"
  - "herramientas de rendimiento, iniciar"
ms.assetid: ba77fcf4-8d78-49f1-b8f3-7dd0acf84306
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# C&#243;mo: Especificar el binario de inicio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Los binarios de perfil, como archivos DLL, debe escribir la información en el cuadro de diálogo de **\<Destino\> Páginas de propiedades** .  Esta información indica donde puede encontrar el proyecto DLL la aplicación que realiza la llamada.  
  
 **Requisitos**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
### Para especificar el ejecutable que se va a iniciar  
  
1.  En el **Explorador de rendimiento**, haga clic con el botón secundario del mouse en el binario de destino y, a continuación, haga clic en **Propiedades**.  
  
2.  En el cuadro de diálogo **Páginas de propiedades**, haga clic en las propiedades de **Iniciar**.  
  
3.  Active la casilla **Reemplazar configuración del proyecto**.  
  
4.  En el cuadro de texto **Ejecutable para iniciar**, especifique la ubicación del archivo.  
  
5.  En el cuadro de texto **Argumentos**, especifique los argumentos necesarios para iniciar la aplicación.  
  
6.  En el cuadro de texto **Directorio de trabajo**, especifique la ubicación del directorio.  
  
7.  Haga clic en **Aceptar**.  
  
## Vea también  
 [Configurar sesiones de rendimiento](../profiling/configuring-performance-sessions.md)