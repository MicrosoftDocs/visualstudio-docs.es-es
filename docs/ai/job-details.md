---
title: Visualización de trabajos recientes
description: Sepa que una vez que los trabajos se envían, puede ver la lista de trabajos para conocer su estado, duración, etc.
ms.custom: SEO-VS-2020
author: jillre
ms.author: jillfra
manager: jmartens
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: 13d78913e0d5d708c5e75a80611ae9cc1c2f7366
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841437"
---
# <a name="view-recent-job-performance-and-details"></a>Ver el rendimiento y los detalles de trabajos recientes

Una vez que se envían los trabajos, puede ver la lista de trabajos para ver su estado, duración y mucho más.

1. En el **Explorador de servidores**, expanda el contexto de ejecución específico.
2. Haga doble clic en **Trabajos**.
3. Verá la lista de trabajos enviados a ese contexto de ejecución.
4. Seleccione un **Trabajo** determinado en la lista para ver los detalles.

![Supervisar trabajos](media/job-details/monitor-jobs.png)

> El historial de los trabajos enviados a las máquinas virtuales de Linux se almacena en el directorio /tmp de la máquina virtual. Por tanto, cada vez que se reinicia, se borra el historial de trabajos. Para un registro permanente del historial de trabajos, configure la máquina virtual como un contexto de ejecución en Azure Machine Learning y después envíe el trabajo a Azure Machine Learning (y seleccione la máquina virtual como el contexto de ejecución).
