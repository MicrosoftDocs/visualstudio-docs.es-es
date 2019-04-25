---
title: 'Error: IIS ha interrumpido el proceso de trabajo del sitio Web | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
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
ms.openlocfilehash: 2d89eabec0c199b1b8df7eeb78d0e629d4a70b2e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60072661"
---
# <a name="error-web-site-worker-process-has-been-terminated-by-iis"></a>Error: IIS ha interrumpido el proceso de trabajo del sitio web
El depurador detuvo la ejecución del código en el sitio web. Esto hizo que Internet Information Services (IIS) creyera que el proceso de trabajo había dejado de responder. Por consiguiente, IIS finalizaron el proceso de trabajo.

 Para seguir depurando, debe configurar IIS para permitir que continúe el proceso de trabajo. Este mensaje de error no aparece con las versiones de IIS anteriores a IIS 7.

### <a name="to-configure-iis-7-to-allow-the-worker-process-to-continue"></a>Para configurar IIS 7 de manera que el proceso de trabajo pueda continuar

1. Abra la ventana **Herramientas administrativas**.

   1. Haga clic en **Inicio** y después elija **Panel de control**.

   2. En el **Panel de control**, elija **Cambiar a Vista clásica** si es necesario y, a continuación, haga doble clic en **Herramientas administrativas**.

2. En la ventana **Herramientas administrativas**, haga doble clic en **Administrador de Internet Information Services (IIS)**.

    Se abrirá el Administrador de IIS.

3. En el panel **Conexiones**, expanda el nodo \<nombre del equipo> si es necesario.

4. En el nodo \<nombre del equipo>, haga clic en **Grupos de aplicaciones**.

5. En la lista **Grupos de aplicaciones**, haga clic con el botón derecho en el nombre del grupo en el que se ejecuta la aplicación y, a continuación, haga clic en **Configuración avanzada**.

6. En el cuadro de diálogo **Configuración avanzada**, busque la sección **Modelo de proceso** y realice una de las acciones siguientes:

   - Establezca **Ping habilitado** en **False**.

   - Establezca **Tiempo máximo de respuesta de ping** en un valor mayor de 90 segundos.

     Si establece **Ping habilitado** en **False**, IIS dejará de comprobar si el proceso de trabajo todavía se está ejecutando y lo mantendrá activo hasta que detenga el proceso depurado. Establecer **Tiempo máximo de respuesta de ping** en un valor grande permite a IIS seguir supervisando el proceso de trabajo.

7. Haga clic en **Aceptar** para cerrar el cuadro de diálogo **Configuración avanzada**.

8. Cierre el Administrador de IIS y la ventana **Herramientas administrativas**.

## <a name="see-also"></a>Vea también
- [Errores de la depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)