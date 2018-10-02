---
ms.technology: vs-ai-tools
ms.openlocfilehash: d52ed79b28794a3bc1532822e0eb75b6277314b2
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44280706"
---
# <a name="browse-storage-to-upload-data-or-download-models-and-logs"></a>Buscar en almacenamiento para cargar datos o descargar registros y modelos

Puede buscar en todo el almacenamiento en el equipo remoto o recurso compartido de archivos de Azure para habilitar la carga de datos o la descarga de modelos y registros. O bien, si quiere acceder a los registros y salidas de trabajo de un trabajo específico, también puede hacerlo en el explorador de trabajos.

## <a name="to-access-all-data-on-the-remote-machine-or-file-share"></a>Para obtener acceso a todos los datos en el equipo remoto o recurso compartido de archivos
1. Abra el **Explorador de servidores**.
2. Expanda el equipo remoto o el contexto de ejecución Batch AI.
3. Haga clic con el botón derecho en **Almacenamiento** y después haga clic en **Examinar**.

    ![storage](media\manage-storage\browse-storage.png)

## <a name="to-access-job-specific-data-on-the-remote-machine-or-file-share"></a>Para acceder a datos específicos del trabajo en el equipo remoto o recurso compartido de archivos
1. Abra el [Historial de trabajos](job-details.md)
2. Seleccione el trabajo.
3. Haga clic en **Carpeta de trabajo** o en **StdOut o Stderr** para obtener acceso rápido a estos archivos de registro importantes.

    ![storage](media\manage-storage\job-workingfolder.png)
