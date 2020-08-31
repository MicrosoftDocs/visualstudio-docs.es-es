---
title: 'Error: No tiene permiso para inspeccionar la identidad del proceso | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: error-reference
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
ms.openlocfilehash: e91745b8910a9e87ccd4a22fe09c6764a2ab4c6a
ms.sourcegitcommit: de98ed7edc81383e47b87ae6e61143fbbbe7bc56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/21/2020
ms.locfileid: "88706534"
---
# <a name="error-you-do-not-have-permission-to-inspect-the-process39s-identity"></a>Error: No tiene permiso para inspeccionar la identidad del proceso
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

## <a name="see-also"></a>Vea también
- [Errores de la depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)