---
ms.technology: vs-ai-tools
ms.openlocfilehash: b7c8de18ba0083d31287fe862ab0015cb210bce1
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44279640"
---
# <a name="view-recent-job-performance-and-details"></a>Ver el rendimiento y los detalles de trabajos recientes
Una vez que se envían los trabajos, puede ver la lista de trabajos para ver su estado, duración y mucho más.

1. En el **Explorador de servidores**, expanda el contexto de ejecución específico.
1. Haga doble clic en **Trabajos**.
1. Verá la lista de trabajos enviados a ese contexto de ejecución.
1. Seleccione un **Trabajo** determinado en la lista para ver los detalles.

![Supervisar trabajos](media\job-details\monitor-jobs.png)

> El historial de los trabajos enviados a las máquinas virtuales de Linux se almacena en el directorio /tmp de la máquina virtual. Por tanto, cada vez que se reinicia, se borra el historial de trabajos. Para un registro permanente del historial de trabajos, configure la máquina virtual como un contexto de ejecución en Azure Machine Learning y después envíe el trabajo a Azure Machine Learning (y seleccione la máquina virtual como el contexto de ejecución).