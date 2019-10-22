---
title: Búsqueda en el almacenamiento para cargar datos
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 8990252f78a9e89b9bdaa825d5443e4d38d2ae89
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62548237"
---
# <a name="browse-storage-to-upload-data-or-download-models-and-logs"></a>Buscar en almacenamiento para cargar datos o descargar registros y modelos

Puede buscar en todo el almacenamiento en el equipo remoto o recurso compartido de archivos de Azure para habilitar la carga de datos o la descarga de modelos y registros. O bien, si quiere acceder a los registros y salidas de trabajo de un trabajo específico, también puede hacerlo en el explorador de trabajos.

## <a name="to-access-all-data-on-the-remote-machine-or-file-share"></a>Para obtener acceso a todos los datos en el equipo remoto o recurso compartido de archivos

1. Abra el **Explorador de servidores**.
2. Expanda el equipo remoto o el contexto de ejecución Batch AI.
3. Haga clic con el botón derecho en **Almacenamiento** y después haga clic en **Examinar**.

    ![storage](media/manage-storage/browse-storage.png)

## <a name="to-access-job-specific-data-on-the-remote-machine-or-file-share"></a>Para acceder a datos específicos del trabajo en el equipo remoto o recurso compartido de archivos

1. Abra el [Historial de trabajos](job-details.md)
2. Seleccione el trabajo.
3. Haga clic en **Carpeta de trabajo** o en **StdOut o Stderr** para obtener acceso rápido a estos archivos de registro importantes.

    ![storage](media/manage-storage/job-workingfolder.png)