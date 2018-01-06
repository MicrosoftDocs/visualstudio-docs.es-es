---
title: Mostrar archivos mediante el comando Abrir archivo | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project types, supporting Open File command
- Open File command
- persistence, supporting Open File command
ms.assetid: 4fff0576-b2f3-4f17-9769-930f926f273c
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 75d714399f851aa479f398064e576790c793fffa
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="displaying-files-by-using-the-open-file-command"></a>Mostrar archivos mediante el comando Abrir archivo
Los siguientes pasos describen cómo el IDE controla la **archivos abiertos** comando, que está disponible en la **archivo** menú en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Los pasos también describen cómo proyectos deben responder a las llamadas que se originan en este comando.  
  
 Cuando un usuario hace clic en el **archivos abiertos** comando el **archivo** menú y selecciona un archivo de la **archivos abiertos** se produce el siguiente proceso de cuadro de diálogo.  
  
1.  Con la tabla document ejecución, el IDE determina si el archivo ya está abierto en un proyecto.  
  
    -   Si el archivo está abierto, el IDE reaparece la ventana.  
  
    -   Si el archivo no está abierto, el IDE llama <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> para consultar cada proyecto para determinar qué proyecto puede abrir el archivo.  
  
        > [!NOTE]
        >  En la implementación de proyecto de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>, proporcione un valor de prioridad que indica el nivel en el que el proyecto abre el archivo. Valores de prioridad se proporcionan en el <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> enumeración.  
  
2.  Cada proyecto responde con un nivel de prioridad que indica la importancia coloca en la que se va al proyecto para abrir el archivo.  
  
3.  El IDE usa los siguientes criterios para determinar qué proyecto abre el archivo:  
  
    -   El proyecto que responde con la prioridad más alta (DP_Intrinsic) abre el archivo. Si más de un proyecto responde con esta prioridad, el primer proyecto responder abre el archivo.  
  
    -   Si no responde de proyecto con la prioridad más alta (DP_Intrinsic), pero responden de todos los proyectos con la prioridad mismo, inferior, el proyecto activo abre el archivo. Si no hay ningún proyecto está activo, el primer proyecto responder abre el archivo.  
  
    -   Si no hay ningún proyecto de notificaciones la titularidad del archivo (DP_Unsupported), el proyecto archivos varios abre el archivo.  
  
         Si se crea una instancia del proyecto de archivos varios, el proyecto siempre responde con el valor DP_CanAddAsExternal. Este valor indica que el proyecto puede abrir el archivo. Este proyecto se utiliza para alojar archivos abiertos que no están en cualquier otro proyecto. La lista de elementos de este proyecto no es persistente; Este proyecto está visible en **el Explorador de soluciones** sólo cuando se utiliza para abrir un archivo.  
  
         Si el proyecto archivos varios no indica que puede abrir el archivo, no se ha creado una instancia del proyecto. En este caso, el IDE crea una instancia del proyecto de archivos varios e indica el proyecto para abrir el archivo.  
  
4.  Tan pronto como el IDE determina qué proyecto abre el archivo, llama a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> método en ese proyecto.  
  
5.  El proyecto, a continuación, tiene la posibilidad de abrir el archivo mediante un editor específico del proyecto o un editor estándar. Para obtener más información, consulte [Cómo: abrir editores específica del proyecto](../../extensibility/how-to-open-project-specific-editors.md) y [Cómo: abrir editores estándar](../../extensibility/how-to-open-standard-editors.md), respectivamente.  
  
## <a name="see-also"></a>Vea también  
 [Visualización de archivos mediante el abierto con el comando](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)   
 [Abrir y guardar elementos de proyecto](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Cómo: abrir editores específica del proyecto](../../extensibility/how-to-open-project-specific-editors.md)   
 [Apertura de editores estándar](../../extensibility/how-to-open-standard-editors.md)