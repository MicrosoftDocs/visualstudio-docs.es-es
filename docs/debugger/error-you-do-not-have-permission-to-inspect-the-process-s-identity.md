---
title: 'Error: no tiene permiso para inspeccionar la identidad del&#39;proceso s | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cad229f80676c3d1f7a7d23ad7a29729c834929b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736221"
---
# <a name="error-you-do-not-have-permission-to-inspect-the-process39s-identity"></a>Error: no tiene permiso para inspeccionar la identidad del&#39;proceso.
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

7. En la ventana **propiedades de Terminal Services** , vaya a la pestaña **General** y establezca **tipo de inicio** en **manual**.

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

## <a name="see-also"></a>Vea también
- [Errores de la depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)