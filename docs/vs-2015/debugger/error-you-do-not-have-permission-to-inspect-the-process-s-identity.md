---
title: 'Error: No tiene permiso para inspeccionar la identidad del proceso | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 6233d060-85b8-42be-ae5f-bde7e1d0f241
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d66eacb1b7f5205ea430d7154f67d05bdd047a74
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157520"
---
# <a name="error-you-do-not-have-permission-to-inspect-the-process39s-identity"></a>Error: No tiene permiso para inspeccionar la identidad del proceso
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

No tiene permiso para inspeccionar la identidad del proceso. Probablemente se deba a la configuración del sistema.  
  
 El depurador no pudo inspeccionar la identidad del proceso, información necesaria para depurar. La causa más probable es que se haya deshabilitado Terminal Services. Terminal Services está habilitado de forma predeterminada. Siga estos pasos para volver a habilitar Terminal Services.  
  
### <a name="to-enable-terminal-services"></a>Para habilitar Terminal Services  
  
1. Haga clic en **Inicio** y después elija **Panel de control**.  
  
2. En el Panel de control, elija **Cambiar a Vista clásica** si es necesario y, a continuación, haga doble clic en **Herramientas administrativas**.  
  
3. En la ventana **Herramientas administrativas**, haga doble clic en **Administración de equipos**.  
  
4. En la ventana Administración de equipos, expanda el nodo **Servicios y Aplicaciones**.  
  
5. En **Servicios y Aplicaciones**, haga clic en **Servicios**.  
  
     Se mostrará una lista de servicios en el panel derecho.  
  
6. En la lista **Servicios**, haga clic con el botón derecho en **Terminal Services** y después elija **Propiedades**.  
  
7. En la ventana **Propiedades de Servicios de Terminal Server**, vaya a la pestaña **General** y establezca **Tipo de inicio** en **Manual**.  
  
8. Haga clic en **Aceptar**.  
  
9. Reinicie el equipo.  
  
     Este procedimiento no habilita automáticamente Escritorio remoto. Si desea habilitar Escritorio remoto en su equipo, realice el siguiente procedimiento adicional.  
  
### <a name="to-enable-remote-desktop"></a>Para habilitar Escritorio remoto  
  
1. Haga clic en **Inicio** y, a continuación, haga clic con el botón derecho en **Mi PC**.  
  
2. Elija **Propiedades**.  
  
     Se mostrará la ventana **Propiedades del sistema**.  
  
3. Haga clic en **Remoto**.  
  
4. En **Escritorio remoto**, seleccione **Permitir que los usuarios se conecten de manera remota a este equipo**.  
  
5. Haga clic en **Aceptar**.  
  
## <a name="see-also"></a>Consulte también  
 [Errores de la depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)
