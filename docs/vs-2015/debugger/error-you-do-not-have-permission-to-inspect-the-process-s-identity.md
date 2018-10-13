---
title: 'Error: No tiene permiso para inspeccionar el proceso&#39;identidad s | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 6233d060-85b8-42be-ae5f-bde7e1d0f241
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7577ac0c2d6b876c3055a90a915e48ea2177bc5b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49196916"
---
# <a name="error-you-do-not-have-permission-to-inspect-the-process39s-identity"></a>Error: No tiene permiso para inspeccionar el proceso&#39;identidad s
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

No tiene permiso para inspeccionar la identidad del proceso. Probablemente se deba a la configuración del sistema.  
  
 El depurador no pudo inspeccionar la identidad del proceso, información necesaria para depurar. La causa más probable es que se haya deshabilitado Terminal Services. Terminal Services está habilitado de forma predeterminada. Siga estos pasos para volver a habilitar Terminal Services.  
  
### <a name="to-enable-terminal-services"></a>Para habilitar Terminal Services  
  
1.  Haga clic en **iniciar** y, a continuación, elija **Panel de Control**.  
  
2.  En el Panel de Control, elija **cambiar a vista clásica**, si es necesario y, a continuación, haga doble clic en **herramientas administrativas**.  
  
3.  En el **herramientas administrativas** ventana, haga doble clic en **administración de equipos**.  
  
4.  En la ventana Administración de equipos, expanda el **servicios y aplicaciones** nodo.  
  
5.  En el **servicios y aplicaciones**, haga clic en **servicios**.  
  
     Se mostrará una lista de servicios en el panel derecho.  
  
6.  En el **servicios** lista, haga clic en **servicios de Terminal Server** y, a continuación, elija **propiedades**.  
  
7.  En el **propiedades de Terminal Services** ventana, vaya a la **General** pestaña y establezca **tipo de inicio** a **Manual**.  
  
8.  Haga clic en **Aceptar**.  
  
9. Reinicie el equipo.  
  
     Este procedimiento no habilita automáticamente Escritorio remoto. Si desea habilitar Escritorio remoto en su equipo, realice el siguiente procedimiento adicional.  
  
### <a name="to-enable-remote-desktop"></a>Para habilitar Escritorio remoto  
  
1.  Haga clic en **iniciar** y, a continuación, haga clic en **Mi PC**.  
  
2.  Elija **Propiedades**.  
  
     El **las propiedades del sistema** se muestra la ventana.  
  
3.  Haga clic en **remoto**.  
  
4.  En **escritorio remoto**, seleccione **permiten a los usuarios conectarse remotamente a este equipo**.  
  
5.  Haga clic en **Aceptar**.  
  
## <a name="see-also"></a>Vea también  
 [Errores de la depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)



