---
title: 'Error: proceso de trabajo del sitio Web ha finalizado por IIS | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.web_server_process_terminated
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 5707b972-71a6-4cc6-ab99-c7c00ca8628c
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 02eca2f832bc88caddd98b14b6615310eef01600
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="error-web-site-worker-process-has-been-terminated-by-iis"></a>Error: IIS ha interrumpido el proceso de trabajo del sitio web
El depurador detuvo la ejecución del código en el sitio web. Esto hizo que Internet Information Services (IIS) creyera que el proceso de trabajo había dejado de responder. Por consiguiente, IIS finalizaron el proceso de trabajo.  
  
 Para seguir depurando, debe configurar IIS para permitir que continúe el proceso de trabajo. Este mensaje de error no aparece con las versiones de IIS anteriores a IIS 7.  
  
### <a name="to-configure-iis-7-to-allow-the-worker-process-to-continue"></a>Para configurar IIS 7 de manera que el proceso de trabajo pueda continuar  
  
1.  Abra la **herramientas administrativas** ventana.  
  
    1.  Haga clic en **iniciar**y, a continuación, elija **el Panel de Control**.  
  
    2.  En **el Panel de Control**, elija **cambiar a vista clásica**, si es necesario y, a continuación, haga doble clic en **herramientas administrativas**.  
  
2.  En el **herramientas administrativas** ventana, haga doble clic en **Internet Information Services (IIS) Manager**.  
  
     Se abrirá el Administrador de IIS.  
  
3.  En el **conexiones** panel, expanda el \<nombre_equipo > nodo si es necesario.  
  
4.  En el \<nombre_equipo > nodo, haga clic en **grupos de aplicaciones**.  
  
5.  En el **grupos de aplicaciones** lista, haga clic en el nombre del grupo de la aplicación se ejecuta en y, a continuación, haga clic en **configuración avanzada**.  
  
6.  En el **configuración avanzada** diálogo cuadro, busque la **modelo de proceso** sección y realice una de las siguientes acciones:  
  
    -   Establecer **Ping habilitado** a **False**.  
  
    -   Establecer **tiempo máximo de respuesta de Ping** en un valor mayor que 90 segundos.  
  
     Establecer **Ping habilitado** a **False** IIS dejará de comprobar si el proceso de trabajo sigue ejecutándose y mantiene el proceso de trabajo activo hasta que detenga el proceso depurado. Establecer **tiempo máximo de respuesta de Ping** en un valor grande permite a IIS seguir supervisando el proceso de trabajo.  
  
7.  Haga clic en **Aceptar** para cerrar el **configuración avanzada** cuadro de diálogo.  
  
8.  Cierre el Administrador de IIS y la **herramientas administrativas** ventana.  
  
## <a name="see-also"></a>Vea también  
 [Errores de la depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)