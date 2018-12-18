---
title: Visualización de archivos mediante el comando Abrir archivo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open File command
- Open File command
- persistence, supporting Open File command
ms.assetid: 4fff0576-b2f3-4f17-9769-930f926f273c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 425433c3d67e654398fde1609b3f9c4d54e63648
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/03/2018
ms.locfileid: "39498730"
---
# <a name="display-files-by-using-the-open-file-command"></a>Mostrar archivos mediante el comando Abrir archivo
Los pasos siguientes describen cómo el IDE controla el **abrir archivo** comando, que está disponible en el **archivo** menú [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. También se describe cómo los proyectos deben responder a las llamadas que proceden de este comando.  
  
 Cuando un usuario hace clic en el **abrir archivo** comando el **archivo** menú y selecciona un archivo desde el **abrir archivo** cuadro de diálogo, que se produce el siguiente proceso:  
  
1.  Uso de la tabla de documentos en ejecución, el IDE determina si el archivo ya está abierto en un proyecto.  
  
    -   Si el archivo está abierto, el IDE reaparece la ventana.  
  
    -   Si el archivo no está abierto, el IDE llama <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> para cada proyecto para determinar qué proyecto puede abrir el archivo de consulta.  
  
        > [!NOTE]
        >  En la implementación del proyecto de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>, proporcione un valor de prioridad que indica el nivel en el que el proyecto abre el archivo. Se proporcionan los valores de prioridad en el <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> enumeración.  
  
2.  Cada proyecto responde con un nivel de prioridad que indica la importancia coloca en la que el proyecto para abrir el archivo.  
  
3.  El IDE usa los siguientes criterios para determinar qué proyecto abre el archivo:  
  
    -   El proyecto al que responde con la prioridad más alta (`DP_Intrinsic`) se abre el archivo. Si más de un proyecto responde con esta prioridad, el primer proyecto responder abre el archivo.  
  
    -   Si no hay ningún proyecto responde con la prioridad más alta (`DP_Intrinsic`), pero todos los proyectos de responder con la prioridad del misma, inferior, el archivo abre el proyecto activo. Si no hay ningún proyecto está activo, el primer proyecto responder abre el archivo.  
  
    -   Si no hay ningún proyecto reclama la propiedad del archivo (`DP_Unsupported`), el archivo abre el proyecto archivos varios.  
  
         Si se crea una instancia del proyecto archivos varios, el proyecto siempre responde con el valor `DP_CanAddAsExternal`. Este valor indica que el proyecto puede abrir el archivo. Este proyecto se usa para alojar los archivos abiertos que no están en cualquier otro proyecto. La lista de elementos de este proyecto no es persistente; Este proyecto está visible en **el Explorador de soluciones** solo cuando se usa para abrir un archivo.  
  
         Si no indica el proyecto archivos varios que puede abrir el archivo, no se ha creado una instancia del proyecto. En este caso, el IDE crea una instancia del proyecto archivos varios e indica al proyecto para abrir el archivo.  
  
4.  Tan pronto como el IDE determina qué proyecto abre el archivo, llama a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> método en ese proyecto.  
  
5.  El proyecto, a continuación, tiene la opción de abrir el archivo con un editor específico del proyecto o un editor estándar. Para obtener más información, consulte [Cómo: abrir editores específicos del proyecto](../../extensibility/how-to-open-project-specific-editors.md) y [Cómo: abrir editores estándar](../../extensibility/how-to-open-standard-editors.md), respectivamente.  
  
## <a name="see-also"></a>Vea también  
 [Mostrar archivos mediante el comando Abrir con](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)   
 [Abrir y guardar elementos de proyecto](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Cómo: abrir editores específicos del proyecto](../../extensibility/how-to-open-project-specific-editors.md)   
 [Cómo: abrir editores estándar](../../extensibility/how-to-open-standard-editors.md)