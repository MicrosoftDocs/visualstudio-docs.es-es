---
title: Visualización de archivos mediante el comando Abrir archivo ( Open File Command) Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708593"
---
# <a name="display-files-by-using-the-open-file-command"></a>Mostrar archivos mediante el comando Abrir archivo
Los pasos siguientes describen cómo el IDE controla el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]comando Abrir **archivo,** que está disponible en el menú **Archivo** de . Los pasos también describen cómo los proyectos deben responder a las llamadas que se originan a partir de este comando.

 Cuando un usuario hace clic en el comando **Abrir archivo** del menú **Archivo** y selecciona un archivo en el cuadro de diálogo **Abrir archivo,** se produce el siguiente proceso:

1. Mediante la tabla de documentos en ejecución, el IDE determina si el archivo ya está abierto en un proyecto.

    - Si el archivo está abierto, el IDE vuelve a aparecer en la ventana.

    - Si el archivo no está abierto, el IDE llama <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> para consultar cada proyecto para determinar qué proyecto puede abrir el archivo.

        > [!NOTE]
        > En la implementación del proyecto de , proporcione un valor de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>prioridad que indique el nivel en el que el proyecto abre el archivo. Los valores de <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> prioridad se proporcionan en la enumeración.

2. Cada proyecto responde con un nivel de prioridad que indica la importancia que le da a ser el proyecto para abrir el archivo.

3. El IDE utiliza los siguientes criterios para determinar qué proyecto abre el archivo:

    - El proyecto que responde con`DP_Intrinsic`la prioridad más alta ( ) abre el archivo. Si más de un proyecto responde con esta prioridad, el primer proyecto que responda abre el archivo.

    - Si ningún proyecto responde con`DP_Intrinsic`la prioridad más alta ( ), pero todos los proyectos responden con la misma prioridad inferior, el proyecto activo abre el archivo. Si no hay ningún proyecto activo, el primer proyecto que responda abre el archivo.

    - Si ningún proyecto reclama la`DP_Unsupported`propiedad del archivo ( ), el proyecto Archivos varios abre el archivo.

         Si se crea una instancia del proyecto Archivos varios, el `DP_CanAddAsExternal`proyecto siempre responde con el valor . Este valor indica que el proyecto puede abrir el archivo. Este proyecto se utiliza para alojar archivos abiertos que no están en ningún otro proyecto. La lista de elementos de este proyecto no se conserva; este proyecto solo está visible en el **Explorador** de soluciones cuando se usa para abrir un archivo.

         Si el proyecto Archivos varios no indica que puede abrir el archivo, no se ha creado una instancia del proyecto. En este caso, el IDE crea una instancia del proyecto Archivos varios e indica al proyecto que abra el archivo.

4. Tan pronto como el IDE determina qué proyecto <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> abre el archivo, llama al método en ese proyecto.

5. A continuación, el proyecto tiene la opción de abrir el archivo mediante un editor específico del proyecto o un editor estándar. Para obtener más información, consulte [Cómo: Abrir editores específicos](../../extensibility/how-to-open-project-specific-editors.md) del proyecto y [Cómo: Abrir editores estándar](../../extensibility/how-to-open-standard-editors.md), respectivamente.

## <a name="see-also"></a>Vea también
- [Mostrar archivos mediante el comando Abrir con](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)
- [Abrir y guardar elementos del proyecto](../../extensibility/internals/opening-and-saving-project-items.md)
- [Cómo: Abrir editores específicos de proyectos](../../extensibility/how-to-open-project-specific-editors.md)
- [Cómo: Abrir editores estándar](../../extensibility/how-to-open-standard-editors.md)
