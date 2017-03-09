---
title: "Proceso de alojamiento (vshost.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "proceso de alojamiento"
  - "vshost.exe"
ms.assetid: c6b9e2be-f18d-4d75-ac52-56d55784734b
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Proceso de alojamiento (vshost.exe)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El proceso de alojamiento es una característica de Visual Studio que mejora el rendimiento de la depuración, habilita la depuración de confianza parcial y permite la evaluación de expresión de tiempo de diseño.  Los archivos del proceso de hospedaje contienen vshost en el nombre de archivo y se colocan en la carpeta de resultados del proyecto.  Para obtener más información, vea [Depuración y proceso host](../debugger/debugging-and-the-hosting-process.md).  
  
> [!NOTE]
>  Alojamiento de los archivos de proceso \(. vshost.exe\) son para uso de Visual Studio y no debe ejecutar directamente o implementado con la aplicación.  
  
## Rendimiento mejorado de la depuración  
 El proceso de hospedaje crea un dominio de aplicación y asocia el depurador a la aplicación.  Realizar estas tareas puede producir un retraso considerable entre el momento en que se inicia la depuración y el momento en que la aplicación comienza a ejecutarse.  El proceso de hospedaje ayuda a aumentar el rendimiento creando el dominio de la aplicación y asociando el depurador en segundo plano, y guardando el estado del dominio de la aplicación y del depurador entre las ejecuciones de la aplicación.  Para obtener más información sobre los dominios de la aplicación, vea [Dominios de aplicación](../Topic/Application%20Domains.md).  
  
## Depuración de confianza parcial  
 Una aplicación se puede especificar como una aplicación de confianza parcial en la [Página de seguridad](../ide/reference/security-page-project-designer.md) del **Diseñador de proyectos**.  Depurar una aplicación de confianza parcial requiere una inicialización especial del dominio de la aplicación.  El proceso de hospedaje controla esta inicialización.  
  
## Evaluación de expresiones en tiempo de diseño  
 La evaluación de expresiones en tiempo de diseño permite probar el código en la ventana **Inmediato** sin tener que ejecutar la aplicación.  El proceso de hospedaje ejecuta este código durante la evaluación de expresiones en tiempo de diseño.  Para obtener más información, vea [Ventana Inmediato](../ide/reference/immediate-window.md).  
  
## Vea también  
 [Depuración y proceso host](../debugger/debugging-and-the-hosting-process.md)   
 [Cómo: Deshabilitar el proceso de alojamiento](../ide/how-to-disable-the-hosting-process.md)   
 [Ventana Inmediato](../ide/reference/immediate-window.md)   
 [Dominios de aplicación](../Topic/Application%20Domains.md)