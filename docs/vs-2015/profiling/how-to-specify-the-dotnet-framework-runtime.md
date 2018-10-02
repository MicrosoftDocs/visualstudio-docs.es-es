---
title: 'Cómo: Especificar runtime de .NET Framework | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Profiling Tools, .NET Framework versions
- .NET Framework versions,profililng
ms.assetid: d39f3579-719a-4f47-a97d-5b4232fe4c64
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 25d7d9e63f5ab5581960f08d32f920b24f2f9906
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47567619"
---
# <a name="how-to-specify-the-net-framework-runtime"></a>Cómo: Especificar runtime de .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Cómo: especificar Runtime de .NET Framework](https://docs.microsoft.com/visualstudio/profiling/how-to-specify-the-dotnet-framework-runtime).  
  
Con el lanzamiento de [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)], las aplicaciones se pueden componer de módulos que se compilaron con versiones diferentes del runtime de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. De forma predeterminada, las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generan perfiles del primer runtime cargado por la aplicación. Puede especificar el runtime del que se deben generar perfiles cuando se inicia una aplicación con el generador de perfiles y al adjuntar el generador de perfiles a una aplicación que ya se está ejecutando.  
  
 **Requisitos**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
### <a name="to-specify-the-net-framework-run-time-to-profile-when-starting-an-application-with-the-profiler"></a>Para especificar el runtime de .NET Framework del que generar perfiles al iniciar una aplicación con el generador de perfiles  
  
1.  En el **Explorador de rendimiento**, haga clic con el botón derecho en la sesión de rendimiento, haga clic en **Propiedades** y después haga clic en **Avanzadas**.  
  
     El cuadro de lista **Versión de CLR de destino** muestra **Automática** y las versiones del runtime de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] que están instaladas en el equipo.  
  
2.  Realice uno de estos pasos:  
  
    -   Haga clic en la versión de CLR de la que desea generar perfiles.  
  
    -   Haga clic en **Automático** para generar perfiles de la primera versión que carga la aplicación.  
  
### <a name="to-specify-the-net-framework-run-time-to-profile-when-attaching-the-profiler-to-an-application"></a>Para especificar el runtime de .NET Framework del que generar perfiles al adjuntar el generador de perfiles a una aplicación  
  
1.  En el menú Analizar, seleccione Generador de perfiles y después haga clic en Asociar/desasociar.  
  
2.  En el cuadro de diálogo Adjuntar generador de perfiles al proceso, haga clic en el proceso del que desea generar perfiles.  
  
     El cuadro de lista **Versión de CLR de destino** muestra **Automático** y las versiones del runtime de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] que están instaladas en el equipo.  
  
3.  Realice uno de estos pasos:  
  
    -   Haga clic en la versión de CLR de la que desea generar perfiles.  
  
    -   Haga clic en **Automático** para generar perfiles de la versión que se carga cuando el generador de perfiles se adjunta a la aplicación.



