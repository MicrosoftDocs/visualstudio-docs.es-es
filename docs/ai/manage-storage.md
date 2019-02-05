---
title: Búsqueda en el almacenamiento para cargar datos
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.service: multiple
ms.workload:
- multiple
ms.openlocfilehash: 44803eea573860074f67d2e97f1160614f452ac5
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54766386"
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