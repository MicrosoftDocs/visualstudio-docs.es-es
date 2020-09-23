---
title: IIS ha interrumpido el proceso de trabajo del sitio web | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.web_server_process_terminated
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
ms.openlocfilehash: f5991bf0b14cf4952303dba599ad47e4c8fd27a9
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852418"
---
# <a name="error-web-site-worker-process-has-been-terminated-by-iis"></a>Error: IIS ha interrumpido el proceso de trabajo del sitio web
El depurador detuvo la ejecución del código en el sitio web. Esto hizo que Internet Information Services (IIS) creyera que el proceso de trabajo había dejado de responder. Por consiguiente, IIS finalizaron el proceso de trabajo.

 Para seguir depurando, debe configurar IIS para permitir que continúe el proceso de trabajo. Este mensaje de error no aparece con las versiones de IIS anteriores a IIS 7.

### <a name="to-configure-iis-7-to-allow-the-worker-process-to-continue"></a>Para configurar IIS 7 de manera que el proceso de trabajo pueda continuar

1. Abra la ventana **Herramientas administrativas**.

   1. Haga clic en **Inicio** y después elija **Panel de control**.

   2. En el **Panel de control**, elija **Cambiar a Vista clásica** si es necesario y, a continuación, haga doble clic en **Herramientas administrativas**.

2. En la ventana **Herramientas administrativas**, haga doble clic en **Administrador de Internet Information Services (IIS)** .

    Se abrirá el Administrador de IIS.

3. En el panel **Conexiones**, expanda el nodo \<computer name> si es necesario.

4. En el nodo \<computer name>, haga clic en **Grupos de aplicaciones**.

5. En la lista **Grupos de aplicaciones**, haga clic con el botón derecho en el nombre del grupo en el que se ejecuta la aplicación y, a continuación, haga clic en **Configuración avanzada**.

6. En el cuadro de diálogo **Configuración avanzada**, busque la sección **Modelo de proceso** y realice una de las acciones siguientes:

   - Establezca **Ping habilitado** en **False**.

   - Establezca **Tiempo máximo de respuesta de ping** en un valor mayor de 90 segundos.

     Si establece **Ping habilitado** en **False**, IIS dejará de comprobar si el proceso de trabajo todavía se está ejecutando y lo mantendrá activo hasta que detenga el proceso depurado. Establecer **Tiempo máximo de respuesta de ping** en un valor grande permite a IIS seguir supervisando el proceso de trabajo.

7. Haga clic en **Aceptar** para cerrar el cuadro de diálogo **Configuración avanzada**.

8. Cierre el Administrador de IIS y la ventana **Herramientas administrativas**.

## <a name="see-also"></a>Vea también
- [Errores de la depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)