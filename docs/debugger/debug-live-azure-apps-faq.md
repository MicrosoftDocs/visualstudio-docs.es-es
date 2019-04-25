---
title: Preguntas frecuentes sobre depuración de instantáneas | Microsoft Docs
ms.date: 11/07/2017
ms.topic: reference
helpviewer_keywords:
- debugger
ms.assetid: 944f1eb0-a74b-4d28-ae2b-a370cd869add
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7ea593ad5f88ba29f6b1c0d7c64a129b8f71c7f5
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58857079"
---
# <a name="frequently-asked-questions-for-snapshot-debugging-in-visual-studio"></a>Preguntas frecuentes sobre depuración de instantáneas en Visual Studio

Aquí se muestra una lista de preguntas que pueden surgir al depurar aplicaciones de Azure en vivo con Snapshot Debugger.

#### <a name="what-is-the-performance-cost-of-taking-a-snapshot"></a>¿Cuál es el costo de rendimiento de la realización de una instantánea?

Cuando Snapshot Debugger captura una instantánea de la aplicación, bifurca el proceso de la aplicación y suspende la copia bifurcada. Al depurar una instantánea, realmente se realiza la depuración de la copia bifurcada del proceso. Este proceso tarda solo entre 10 y 20 milisegundos, pero no copia el montón completo de la aplicación. En su lugar, copia solo la tabla de páginas y establece las páginas para la copia en escritura. Si algunos de los objetos del montón de la aplicación cambian, entonces se copian sus páginas correspondientes. De esa forma, cada instantánea tiene un costo reducido en memoria (del orden de cientos de kilobytes para la mayoría de las aplicaciones).

#### <a name="what-happens-if-i-have-a-scaled-out-azure-app-service-multiple-instances-of-my-app"></a>¿Qué ocurre si tengo una instancia de Azure App Service de escalabilidad horizontal (varias instancias de mi aplicación)?

Si tiene varias instancias de la aplicación, los puntos de instantánea se aplican a cada instancia de forma individual. Solo el primer punto de instantánea que se alcanza con las condiciones especificadas crea una instantánea. Si tiene varios puntos de instantánea, las instantáneas posteriores proceden de la misma instancia que creó la primera instantánea. Los puntos de registro enviados a la ventana de salida solo mostrarán los mensajes de una instancia, mientras que los puntos de registro enviados a los registros de aplicaciones envían mensajes desde cada instancia.

#### <a name="how-does-the-snapshot-debugger-load-symbols"></a>¿Cómo Snapshot Debugger carga los símbolos?

Snapshot Debugger requiere disponer de los símbolos correspondientes para la aplicación ya sea en el entorno local o implementados en Azure App Service. (Los archivos PDB insertados no son compatibles actualmente). Snapshot Debugger descarga los símbolos automáticamente de Azure App Service. A partir de Visual Studio 2017, versión 15.2, la implementación en Azure App Service también supone la implementación de los símbolos de la aplicación.

#### <a name="does-the-snapshot-debugger-work-against-release-builds-of-my-application"></a>¿Snapshot Debugger funciona con las compilaciones de versión de mi aplicación?

Sí; Snapshot Debugger está diseñado para funcionar con las compilaciones de versión. Cuando se coloca un punto de instantánea en una función, esta se vuelve a recompilar en una versión de depuración, de tal forma que se convierte en depurable. Al detener Snapshot Debugger, las funciones se devuelven a la versión de la compilación de versión.

#### <a name="can-logpoints-cause-side-effects-in-my-production-application"></a>¿Los puntos de registro pueden causar efectos secundarios en mi aplicación de producción?

No; los mensajes de registro agregados a la aplicación se evalúan de forma práctica. No pueden causar ningún efecto secundario en la aplicación. Sin embargo, algunas propiedades nativas pueden no estar accesibles para los puntos de registro.

#### <a name="does-the-snapshot-debugger-work-if-my-server-is-under-load"></a>¿Snapshot Debugger funciona si mi servidor está cargado?

Sí, la depuración de instantáneas puede funcionar en los servidores con carga. Snapshot Debugger limita y no captura las instantáneas en situaciones en las que hay una baja cantidad de memoria disponible en el servidor.

#### <a name="how-do-i-uninstall-the-snapshot-debugger"></a>¿Cómo se puede desinstalar Snapshot Debugger?

Puede desinstalar la extensión de sitio de Snapshot Debugger en la instancia de App Service con estos pasos:

1. Desactive la instancia de App Service en Cloud Explorer en Visual Studio o en Azure Portal.
1. Vaya al sitio de Kudu en App Service, es decir, yourappservice.**scm**.azurewebsites.net, y acceda a **Extensiones de sitio**.
1. Haga clic en la X de la extensión de sitio de Snapshot Debugger para quitarla.

#### <a name="why-are-ports-opened-during-a-snapshot-debugger-session"></a>¿Por qué hay puertos abiertos durante una sesión de Snapshot Debugger?

Snapshot Debugger necesita abrir un conjunto de puertos para depurar las instantáneas realizadas en Azure; se trata de los mismos puertos necesarios para la depuración remota. [Puede encontrar la lista de puertos aquí](../debugger/remote-debugger-port-assignments.md).

## <a name="see-also"></a>Vea también

- [Depurar en Visual Studio](../debugger/index.md)
- [Depurar aplicaciones ASP.NET activas con el depurador de instantáneas](../debugger/debug-live-azure-applications.md)
- [Depuración en directo ASP.NET Azure Virtual Machines\Virtual máquinas conjuntos de escalado mediante el depurador de instantáneas](../debugger/debug-live-azure-virtual-machines.md)
- [Depuración en directo ASP.NET Azure Kubernetes con el depurador de instantáneas](../debugger/debug-live-azure-kubernetes.md)
- [Problemas conocidos y solución de problemas de depuración de instantáneas](../debugger/debug-live-azure-apps-troubleshooting.md)