---
title: 'Error: se terminó el proceso de trabajo de sitio Web IIS | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.web_server_process_terminated
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 5707b972-71a6-4cc6-ab99-c7c00ca8628c
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 81396165841b0c23a317a857e73d7adbf88971dc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47579272"
---
# <a name="error-web-site-worker-process-has-been-terminated-by-iis"></a>Error: IIS ha interrumpido el proceso de trabajo del sitio web
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Error: IIS ha interrumpido el proceso de trabajo del sitio Web](https://docs.microsoft.com/visualstudio/debugger/error-web-site-worker-process-has-been-terminated-by-iis).  
  
El depurador detuvo la ejecución del código en el sitio web. Esto hizo que Internet Information Services (IIS) creyera que el proceso de trabajo había dejado de responder. Por consiguiente, IIS finalizaron el proceso de trabajo.  
  
 Para seguir depurando, debe configurar IIS para permitir que continúe el proceso de trabajo. Este mensaje de error no aparece con las versiones de IIS anteriores a IIS 7.  
  
### <a name="to-configure-iis-7-to-allow-the-worker-process-to-continue"></a>Para configurar IIS 7 de manera que el proceso de trabajo pueda continuar  
  
1.  Abra el **herramientas administrativas** ventana.  
  
    1.  Haga clic en **iniciar**y, a continuación, elija **Panel de Control**.  
  
    2.  En **Panel de Control**, elija **cambiar a vista clásica**, si es necesario y, a continuación, haga doble clic en **herramientas administrativas**.  
  
2.  En el **herramientas administrativas** ventana, haga doble clic en **Internet Information Services (IIS) Manager**.  
  
     Se abrirá el Administrador de IIS.  
  
3.  En el **conexiones** panel, expanda el \<nombre_equipo > nodo si es necesario.  
  
4.  En el \<nombre_equipo > nodo, haga clic en **grupos de aplicaciones**.  
  
5.  En el **grupos de aplicaciones** lista, haga clic en el nombre del grupo de la aplicación se ejecuta en y, a continuación, haga clic en **configuración avanzada**.  
  
6.  En el **configuración avanzada** diálogo cuadro, busque la **modelo de proceso** sección y realice una de las siguientes acciones:  
  
    -   Establecer **Ping habilitado** a **False**.  
  
    -   Establecer **tiempo máximo de respuesta de Ping** en un valor que es mayor que 90 segundos.  
  
     Establecer **Ping habilitado** a **False** IIS dejará de comprobar si el proceso de trabajo se sigue ejecutando y que mantiene el proceso de trabajo activo hasta que detenga el proceso depurado. Establecer **tiempo máximo de respuesta de Ping** en un valor grande permite a IIS seguir supervisando el proceso de trabajo.  
  
7.  Haga clic en **Aceptar** para cerrar el **configuración avanzada** cuadro de diálogo.  
  
8.  Cierre el Administrador de IIS y la **herramientas administrativas** ventana.  
  
## <a name="see-also"></a>Vea también  
 [Errores de la depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)



