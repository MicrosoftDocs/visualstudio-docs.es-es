---
title: "C&#243;mo: Deshabilitar el proceso de alojamiento | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "proceso de alojamiento, deshabilitar"
  - "vshost.exe, deshabilitar el proceso de alojamiento"
ms.assetid: 9157488d-737f-454b-8d8d-36f99de38bb0
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# C&#243;mo: Deshabilitar el proceso de alojamiento
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Las llamadas a ciertas API pueden verse afectadas cuando se habilita el proceso de hospedaje.  En estos casos, es necesario deshabilitar el proceso de hospedaje para devolver los resultados correctos.  
  
### Para deshabilitar el proceso de hospedaje  
  
1.  Abra un proyecto ejecutable en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Los proyectos que no generan archivos ejecutables \(por ejemplo, proyectos de biblioteca de clases o de servicio\) no tienen esta opción.  
  
2.  En el menú **Proyecto**, haga clic en **Propiedades**.  
  
3.  Haga clic en la pestaña **Depurar**.  
  
4.  Desactive la casilla **Habilitar el proceso de hospedaje de Visual Studio**.  
  
 Cuando se deshabilita el proceso de hospedaje, varias características de depuración no están disponibles o sufren una disminución de rendimiento.  Para obtener más información, vea [Depuración y proceso host](../debugger/debugging-and-the-hosting-process.md).  
  
 En general, cuando se deshabilita el proceso de hospedaje:  
  
-   Aumenta el tiempo necesario para empezar a depurar las aplicaciones de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
-   No está disponible la evaluación de expresiones en tiempo de diseño.  
  
-   No está disponible la depuración de confianza parcial.  
  
## Vea también  
 [Depuración y proceso host](../debugger/debugging-and-the-hosting-process.md)   
 [Proceso de alojamiento \(vshost.exe\)](../ide/hosting-process-vshost-exe.md)   
 [Builds During Application Development](http://msdn.microsoft.com/es-es/c9497d62-3b7b-4449-88e8-cf27acc9efe6)