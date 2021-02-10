---
title: Búsqueda en el almacenamiento para cargar datos
description: Sepa cómo examinar todo el almacenamiento del equipo remoto o recurso compartido de archivos de Azure para habilitar la carga de datos o la descarga de modelos y registros.
ms.custom: SEO-VS-2020
author: jillre
ms.author: jillfra
manager: jmartens
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: c32fc5f4ceeb090c8c602b01078fd446249f33eb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841424"
---
# <a name="browse-storage-to-upload-data-or-download-models-and-logs"></a>Buscar en almacenamiento para cargar datos o descargar registros y modelos

Puede buscar en todo el almacenamiento en el equipo remoto o recurso compartido de archivos de Azure para habilitar la carga de datos o la descarga de modelos y registros. O bien, si quiere acceder a los registros y salidas de trabajo de un trabajo específico, también puede hacerlo en el explorador de trabajos.

## <a name="to-access-all-data-on-the-remote-machine-or-file-share"></a>Para obtener acceso a todos los datos en el equipo remoto o recurso compartido de archivos

1. Abra el **Explorador de servidores**.
2. Expanda el equipo remoto o el contexto de ejecución Batch AI.
3. Haga clic con el botón derecho en **Almacenamiento** y después haga clic en **Examinar**.

    ![Captura de pantalla del Explorador de servidores con la carpeta Remote Machines (Máquinas remotas) expandida. Almacenamiento está resaltado en el árbol de carpetas y la opción Examinar está seleccionada en el menú contextual.](media/manage-storage/browse-storage.png)

## <a name="to-access-job-specific-data-on-the-remote-machine-or-file-share"></a>Para acceder a datos específicos del trabajo en el equipo remoto o recurso compartido de archivos

1. Abra el [Historial de trabajos](job-details.md)
2. Seleccione el trabajo.
3. Haga clic en **Carpeta de trabajo** o en **StdOut o Stderr** para obtener acceso rápido a estos archivos de registro importantes.

    ![Captura de pantalla de la ventana Explorador de trabajos en el Explorador de servidores. El trabajo train_mnist está seleccionado y también lo está el vínculo Carpeta de trabajo en la sección Job Details (Detalles del trabajo).](media/manage-storage/job-workingfolder.png)
