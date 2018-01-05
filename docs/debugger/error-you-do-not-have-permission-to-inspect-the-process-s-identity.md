---
title: 'Error: No tiene permiso para inspeccionar el proceso &#39; identidad s | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f51087d4f7882c34826942a898328640107a5ac6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="error-you-do-not-have-permission-to-inspect-the-process39s-identity"></a>Error: No tiene permiso para inspeccionar el proceso &#39; identidad s
No tiene permiso para inspeccionar la identidad del proceso. Probablemente se deba a la configuración del sistema.  
  
 El depurador no pudo inspeccionar la identidad del proceso, información necesaria para depurar. La causa más probable es que se haya deshabilitado Terminal Services. Terminal Services está habilitado de forma predeterminada. Siga estos pasos para volver a habilitar Terminal Services.  
  
### <a name="to-enable-terminal-services"></a>Para habilitar Terminal Services  
  
1.  Haga clic en **iniciar** y, a continuación, elija **el Panel de Control**.  
  
2.  En el Panel de Control, elija **cambiar a vista clásica**, si es necesario y, a continuación, haga doble clic en **herramientas administrativas**.  
  
3.  En el **herramientas administrativas** ventana, haga doble clic en **administración de equipos**.  
  
4.  En la ventana Administración de equipos, expanda el **servicios y aplicaciones** nodo.  
  
5.  En el **servicios y aplicaciones**, haga clic en **Services**.  
  
     Se mostrará una lista de servicios en el panel derecho.  
  
6.  En el **servicios** lista, haga clic en **servicios de Terminal Server** y, a continuación, elija **propiedades**.  
  
7.  En el **propiedades Terminal Services** ventana, vaya a la **General** pestaña y establecer **tipo de inicio** a **Manual**.  
  
8.  Haga clic en **Aceptar**.  
  
9. Reinicie el equipo.  
  
     Este procedimiento no habilita automáticamente Escritorio remoto. Si desea habilitar Escritorio remoto en su equipo, realice el siguiente procedimiento adicional.  
  
### <a name="to-enable-remote-desktop"></a>Para habilitar Escritorio remoto  
  
1.  Haga clic en **iniciar** y, a continuación, haga clic en **Mi PC**.  
  
2.  Elija **propiedades**.  
  
     El **propiedades del sistema** se muestra la ventana.  
  
3.  Haga clic en **remoto**.  
  
4.  En **escritorio remoto**, seleccione **permiten a los usuarios conectarse remotamente a este equipo**.  
  
5.  Haga clic en **Aceptar**.  
  
## <a name="see-also"></a>Vea también  
 [Errores de la depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)