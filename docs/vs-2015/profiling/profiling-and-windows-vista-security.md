---
title: Generar perfiles y seguridad en Windows Vista | Microsoft Docs
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
- Profiling Tools,security
- performance tools, security
ms.assetid: 842112fc-b886-4801-8cd7-a25b314b0393
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 736e7a04813a6c56d6cab6d1886171e321d583cb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47581617"
---
# <a name="profiling-and-windows-vista-security"></a>Generar perfiles y seguridad en Windows Vista
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [generación de perfiles y seguridad de Windows Vista](https://docs.microsoft.com/visualstudio/profiling/profiling-and-windows-vista-security).  
  
En función de la configuración de los permisos de acceso de usuario de [!INCLUDE[wiprlhext](../includes/wiprlhext-md.md)] que haya facilitado un administrador de equipo, un usuario puede tener permisos de seguridad para generar perfiles de un proceso en ese equipo. En los siguientes ejemplos se muestran las posibles diferencias existentes entre los usuarios:  
  
-   Algunos usuarios pueden tener acceso a las características avanzadas de generación de perfiles cuando el administrador ha configurado el controlador y el servicio para que se inicien.  
  
-   Los usuarios de dominio pueden tener acceso solo a la generación de perfiles de ejemplo.  
  
-   Algunos usuarios pueden denegar el acceso a la generación de perfiles a todos los demás usuarios.  
  
 Para obtener más información, consulte las opciones ADMIN de [VSPerfCmd](../profiling/vsperfcmd.md).  
  
## <a name="cross-session-profiling"></a>Generación de perfiles entre sesiones  
 La *generación de perfiles entre sesiones* es la capacidad de generar perfiles de un proceso que se ejecuta en una sesión diferente. Por ejemplo, la mayoría de servicios se ejecutan en la sesión 0 y los usuarios no pueden ejecutarse directamente en la sesión 0. Mediante el uso del botón **Adjuntar al proceso** en la barra de herramientas del explorador de rendimiento o la opción /attach de la herramienta de línea de comandos VSPerfCmd, puede generar perfiles de la mayoría de los procesos en otras sesiones de inicio.  
  
 Puede ver una lista de los procesos que están disponibles mediante el establecimiento de las opciones de visibilidad de generación de perfiles entre procesos. Estas opciones están disponibles en la ventana **Adjuntar al proceso** que aparece al hacer clic en **Adjuntar al proceso**:  
  
-   **Mostrar los procesos de todos los usuarios**  
  
     Cuando no se selecciona esta opción, la lista muestra solamente los procesos que pertenecen al usuario actual. Cuando **Mostrar procesos de todos los usuarios** está seleccionada, la lista muestra los procesos de todos los usuarios.  
  
-   **Mostrar los procesos de todas las sesiones**  
  
     Cuando no se selecciona esta opción, la lista muestra los procesos de la sesión actual. Cuando se selecciona esta opción, la lista muestra los procesos de todas las sesiones.  
  
## <a name="see-also"></a>Vea también  
 [Información general](../profiling/overviews-performance-tools.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Cómo: Conectar a procesos en ejecución](http://msdn.microsoft.com/en-us/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4)



