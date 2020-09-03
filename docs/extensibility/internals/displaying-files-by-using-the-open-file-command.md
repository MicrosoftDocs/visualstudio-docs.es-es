---
title: Mostrar archivos mediante el comando Abrir archivo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open File command
- Open File command
- persistence, supporting Open File command
ms.assetid: 4fff0576-b2f3-4f17-9769-930f926f273c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cc18442c55b6989c4d8668e1425fdd62a2d4b1b6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708593"
---
# <a name="display-files-by-using-the-open-file-command"></a>Mostrar archivos mediante el comando Abrir archivo
En los pasos siguientes se describe cómo el IDE controla el comando **Abrir archivo** , que está disponible en el menú **archivo** de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . En los pasos también se describe cómo los proyectos deben responder a las llamadas que se originan desde este comando.

 Cuando un usuario hace clic en el comando **Abrir archivo** en el menú **archivo** y selecciona un archivo en el cuadro de diálogo **Abrir archivo** , se produce el siguiente proceso:

1. Con la tabla de documentos en ejecución, el IDE determina si el archivo ya está abierto en un proyecto.

    - Si el archivo está abierto, el IDE repone la ventana.

    - Si el archivo no está abierto, el IDE llama <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> a para consultar cada proyecto con el fin de determinar qué proyecto puede abrir el archivo.

        > [!NOTE]
        > En la implementación del proyecto de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> , proporcione un valor de prioridad que indique el nivel en el que el proyecto abre el archivo. Los valores de prioridad se proporcionan en la <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> enumeración.

2. Cada proyecto responde con un nivel de prioridad que indica la importancia que supone que el proyecto Abra el archivo.

3. El IDE usa los siguientes criterios para determinar qué proyecto abre el archivo:

    - El proyecto que responde con la prioridad más alta ( `DP_Intrinsic` ) abre el archivo. Si más de un proyecto responde con esta prioridad, el primer proyecto que responda abre el archivo.

    - Si ningún proyecto responde con la prioridad más alta ( `DP_Intrinsic` ), pero todos los proyectos responden con la misma prioridad inferior, el proyecto activo abre el archivo. Si no hay ningún proyecto activo, el primer proyecto que responde abre el archivo.

    - Si ningún proyecto reclama la propiedad del archivo ( `DP_Unsupported` ), el proyecto archivos varios abre el archivo.

         Si se crea una instancia del proyecto de archivos varios, el proyecto siempre responde con el valor `DP_CanAddAsExternal` . Este valor indica que el proyecto puede abrir el archivo. Este proyecto se usa para hospedar archivos abiertos que no están en ningún otro proyecto. La lista de elementos de este proyecto no se conserva; Este proyecto solo es visible en **Explorador de soluciones** cuando se usa para abrir un archivo.

         Si el proyecto archivos varios no indica que puede abrir el archivo, no se ha creado una instancia del proyecto. En este caso, el IDE crea una instancia del proyecto de archivos varios e indica al proyecto que abra el archivo.

4. En cuanto el IDE determina qué proyecto abre el archivo, llama al <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> método en ese proyecto.

5. Después, el proyecto tiene la opción de abrir el archivo mediante un editor específico del proyecto o un editor estándar. Para obtener más información, consulte [Cómo: abrir editores específicos del proyecto](../../extensibility/how-to-open-project-specific-editors.md) y [Cómo: abrir editores estándar](../../extensibility/how-to-open-standard-editors.md), respectivamente.

## <a name="see-also"></a>Consulte también
- [Mostrar archivos mediante el comando abrir con](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)
- [Abrir y guardar elementos de proyecto](../../extensibility/internals/opening-and-saving-project-items.md)
- [Cómo: abrir editores específicos del proyecto](../../extensibility/how-to-open-project-specific-editors.md)
- [Cómo: abrir editores estándar](../../extensibility/how-to-open-standard-editors.md)
