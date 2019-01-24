---
title: Preguntas más frecuentes sobre depuración de instantáneas | Microsoft Docs
ms.date: 11/07/2017
ms.topic: reference
helpviewer_keywords:
- debugger
ms.assetid: 944f1eb0-a74b-4d28-ae2b-a370cd869add
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ce6f242486afd82508e60d2e20c053735e61d6f3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53924168"
---
# <a name="frequently-asked-questions-for-snapshot-debugging-in-visual-studio"></a>Preguntas más frecuentes sobre depuración de instantáneas en Visual Studio

Esta es una lista de preguntas que es posible que surgen al depurar aplicaciones de Azure en vivo mediante el depurador de instantáneas.

#### <a name="what-is-the-performance-cost-of-taking-a-snapshot"></a>¿Qué es el costo de rendimiento de tomar una instantánea?

Cuando el depurador de instantáneas se captura una instantánea de la aplicación, es el proceso de la aplicación de bifurcación y suspender la copia bifurcada. Cuando se depura una instantánea, que está depurando en la copia del proceso bifurcada. Este proceso tarda sólo 10-20 milisegundos, pero no copia el montón completo de la aplicación. En su lugar, solo la tabla de páginas de copia y establece las páginas de copia en escritura. Si algunos de los objetos de la aplicación en el cambio de montón, a continuación, se copian sus respectivas páginas. Por lo tanto, cada instantánea tiene un pequeño costo en memoria (del orden de cientos de kilobytes para la mayoría de las aplicaciones). 

#### <a name="what-happens-if-i-have-a-scaled-out-azure-app-service-multiple-instances-of-my-app"></a>¿Qué ocurre si tengo una escalada Azure App Service (varias instancias de mi aplicación)?

Cuando tiene varias instancias de la aplicación, los puntos de acoplamiento se aplican a cada instancia única. Solo el primer punto de acoplamiento a acertar con las condiciones especificadas, crea una instantánea. Si tiene varios puntos de acoplamiento, instantáneas siguientes proceden de la misma instancia que creó la primera instantánea. Puntos de registro enviados a la ventana de salida sólo mostrará los mensajes de una instancia, mientras los puntos de registro enviados en registros de aplicaciones envían mensajes desde todas las instancias. 

#### <a name="how-does-the-snapshot-debugger-load-symbols"></a>¿Cómo el depurador de instantáneas cargar símbolos?

El depurador de instantáneas requiere que haya los símbolos coincidentes para la aplicación local o implementada a Azure App Service. (Los archivos PDB incrustados no admiten actualmente.) El depurador de instantáneas se descarga automáticamente los símbolos de Azure App Service. A partir de Visual Studio 2017 versión 15.2, implementar en Azure App Service también implementa los símbolos de la aplicación.

#### <a name="does-the-snapshot-debugger-work-against-release-builds-of-my-application"></a>¿Funciona el depurador de instantáneas en las compilaciones de versión de mi aplicación?

Sí: el depurador de instantáneas está diseñado para trabajar con las versiones de lanzamiento. Cuando un punto de acoplamiento se coloca en una función, se vuelve a compilar la función a una versión de depuración, lo que va a depurar. Cuando se detiene el depurador de instantáneas, se devuelven las funciones a su versión de lanzamiento. 

#### <a name="can-logpoints-cause-side-effects-in-my-production-application"></a>¿Puntos de registro pueden provocar efectos secundarios en mi aplicación de producción?

No; se evalúa de prácticamente cualquier mensaje de registro que se agrega a la aplicación. No produzcan efectos secundarios en la aplicación. Sin embargo, algunas propiedades nativas no esté accesibles con puntos de registro. 

#### <a name="does-the-snapshot-debugger-work-if-my-server-is-under-load"></a>¿Funciona el depurador de instantáneas si mi servidor está bajo carga?

Sí, la depuración de instantáneas puede funcionar en servidores con carga. El depurador de instantáneas limita y no captura las instantáneas en situaciones donde hay una cantidad baja de memoria libre en el servidor.

#### <a name="how-do-i-uninstall-the-snapshot-debugger"></a>¿Cómo se puede desinstalar el depurador de instantáneas?

Puede desinstalar la extensión del sitio Snapshot Debugger en App Service con los pasos siguientes:

1. Desactivar la aplicación de servicio a través de Cloud Explorer en Visual Studio o Azure portal.
1. Navegue al sitio de Kudu de App Service (es decir, yourappservice. **SCM**. azurewebsites.net) y vaya a **extensiones de sitio**.
1. Haga clic en la X de la extensión del sitio Snapshot Debugger para quitarlo.

## <a name="see-also"></a>Vea también

[Depurar en Visual Studio](../debugger/index.md)  
[Depurar aplicaciones ASP.NET activas con el depurador de instantáneas](../debugger/debug-live-azure-applications.md)  
[Problemas conocidos y solución de problemas de depuración de instantáneas](../debugger/debug-live-azure-apps-troubleshooting.md)
