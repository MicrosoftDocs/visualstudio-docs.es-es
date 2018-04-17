---
title: Preguntas más frecuentes sobre depuración instantánea | Documentos de Microsoft
ms.date: 11/07/2017
ms.technology:
- vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- debugger
ms.assetid: 944f1eb0-a74b-4d28-ae2b-a370cd869add
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: db887f783cf205bb7951cde985fa371ab1ab755c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="frequently-asked-questions-for-snapshot-debugging-in-visual-studio"></a>Preguntas más frecuentes para la depuración instantánea en Visual Studio

Esta es una lista de preguntas que puede surgir al depurar aplicaciones de Azure en vivo mediante el depurador de instantánea.

#### <a name="what-is-the-performance-cost-of-taking-a-snapshot"></a>¿Cuál es el costo de rendimiento de tomar una instantánea?

Cuando el depurador de instantánea captura una instantánea de la aplicación, es el proceso de la aplicación de los de bifurcación y suspender la copia bifurcada. Cuando se depura una instantánea, se depura con la copia bifurcada del proceso. Este proceso tarda sólo 10 a 20 milisegundos pero no copia el montón completo de la aplicación; en su lugar, se copia la tabla de la página y establece las páginas para copia por escritura. Si algunos de los objetos de la aplicación en el cambio de montón, a continuación, se copian sus páginas correspondientes. Cada instantánea, por tanto, tiene un costo muy pequeño de en memoria (en el orden cientos de kilobytes para la mayoría de las aplicaciones). 

#### <a name="what-happens-if-i-have-a-scaled-out-azure-app-service-multiple-instances-of-my-app"></a>¿Qué ocurre si tengo un servicio de aplicaciones de Azure de escala horizontal (varias instancias de la aplicación)?

Si tiene varias instancias de la aplicación, snappoints se aplican a cada instancia única. Solo el primer snappoint se alcanza únicamente con las condiciones especificadas, crea una instantánea. Si tiene varios snappoints, instantáneas posteriores proceden de la misma instancia que se crea la primera instantánea. Logpoints que se envían a la ventana de salida solo mostrará mensajes de una instancia, mientras logpoints enviados a registros de aplicación enviar mensajes desde cada instancia. 

#### <a name="how-does-the-snapshot-debugger-load-symbols"></a>¿Cómo cargar el depurador de instantánea de los símbolos?

El depurador de instantáneas requiere que dispone de los símbolos que coinciden para la aplicación ya sea localmente o implementada en el servicio de aplicaciones de Azure (archivos PDB incrustados no se admiten). El depurador de instantánea descarga automáticamente los símbolos de su servicio de aplicaciones de Azure. A partir de Visual Studio de 2017 versión 15,2, implementar el servicio de aplicación de Azure también implementa los símbolos de la aplicación.

#### <a name="does-the-snapshot-debugger-work-against-release-builds-of-my-application"></a>¿Funciona el depurador de instantánea con versiones de lanzamiento de mi aplicación?

Sí: el depurador de instantánea está diseñado para trabajar con versiones de lanzamiento. Cuando se coloca un snappoint en una función, se vuelve a compilar la función a una versión de depuración, lo que va a depurar. Cuando se detiene el depurador de instantánea, las funciones se devuelven a su versión de lanzamiento. 

#### <a name="can-logpoints-cause-side-effects-in-my-production-application"></a>¿Logpoints pueden producir efectos secundarios en mi aplicación de producción?

No: los mensajes de registro que agrega a la aplicación se evalúan prácticamente. No se producen efectos secundarios en la aplicación. Sin embargo, algunas propiedades nativas pueden no estar accesibles con logpoints. 

#### <a name="does-the-snapshot-debugger-work-if-my-server-is-under-load"></a>¿Funciona el depurador de instantánea si mi servidor está bajo carga?

Sí, la depuración instantánea puede trabajar para servidores bajo carga. El depurador de instantánea limita y no captura las instantáneas en situaciones donde hay una cantidad baja de memoria libre en el servidor.

#### <a name="how-do-i-uninstall-the-snapshot-debugger"></a>¿Cómo se puede desinstalar el depurador de instantáneas?

Puede desinstalar la extensión del depurador de instantánea de sitio en el servicio de aplicaciones con los pasos siguientes:

1. Desactivar el servicio de aplicaciones mediante el Explorador de nube en Visual Studio o en el Portal de Azure.
1. Navegue al sitio de Kudu del servicio de aplicación (es decir, yourappservice. **SCM**. azurewebsites.net) y navegue hasta **extensiones de sitio**.
1. Haga clic en la X en la extensión del depurador de instantánea de sitio para quitarlo.

## <a name="see-also"></a>Vea también

[Depurar en Visual Studio](../debugger/index.md)  
[Depurar aplicaciones ASP.NET en directo con el depurador de instantánea](../debugger/debug-live-azure-applications.md)  
[Solución de problemas y problemas conocidos para la depuración instantánea](../debugger/debug-live-azure-apps-troubleshooting.md)
