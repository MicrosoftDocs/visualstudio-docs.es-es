---
title: Filtrar Apertura de editores estándar | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], opening
- projects [Visual Studio SDK], opening standard editors
ms.assetid: d5ce10f9-047a-4b74-aa1d-295128898b89
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f75a64929074be45645de529ccb05f52f9d04ef9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58996646"
---
# <a name="how-to-open-standard-editors"></a>Filtrar Abrir editores estándar
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Al abrir un editor estándar, permite que el IDE de determinar un editor estándar para un tipo de archivo designado, en lugar de especificar un editor específico del proyecto para el archivo.  
  
 Complete el procedimiento siguiente para implementar el <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> método. Se abrirá un archivo de proyecto en un editor estándar.  
  
### <a name="to-implement-the-openitem-method-with-a-standard-editor"></a>Para implementar el método OpenItem con un editor estándar  
  
1.  Llame a <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> (`RDT_EditLock`) para determinar si el archivo de objeto de datos de documento ya está abierto.  
  
2.  Si el archivo ya está abierto, reaparece el archivo mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> método, especificando un valor de `IDO_ActivateIfOpen` para el `grfIDO` parámetro.  
  
     Si el archivo está abierto y el documento es propiedad de un proyecto diferente que el proyecto que realiza la llamada, el proyecto recibe una advertencia de que el editor que se está abriendo proviene de otro proyecto. A continuación, aparece la ventana de archivo.  
  
3.  Si el documento no está abierto o no en la tabla de documentos en ejecución, llame a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> método (`OSE_ChooseBestStdEditor`) para abrir un editor estándar para el archivo.  
  
     Cuando se llama al método, el IDE realiza las siguientes tareas:  
  
    1.  El IDE examina los editores / {guidEditorType} / subclave de extensiones en el registro para determinar qué editor puede abrir el archivo y tiene la máxima prioridad para realizar esta acción.  
  
    2.  Una vez que el IDE ha determinado qué editor puede abrir el archivo, el IDE llama <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>. Implementación del editor de este método devuelve la información necesaria para el IDE llamar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> y el documento recién abierto del sitio.  
  
    3.  Por último, el IDE carga el documento mediante la interfaz de persistencia habituales, como <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>.  
  
    4.  Si el IDE anteriormente ha determinado que la jerarquía o elemento de la jerarquía está disponible, el IDE llama <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> método en el proyecto para obtener un contexto de nivel de proyecto <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> puntero que se pasan en con el <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> llamada al método.  
  
4.  Devolver un <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> puntero en el IDE cuando el IDE llama <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> en el proyecto si desea permitir que el editor obtener el contexto del proyecto.  
  
     Llevar a cabo este paso permite a los servicios adicionales de oferta de proyecto en el editor.  
  
     Si la vista de documento o el objeto de vista de documento se ha ubicado correctamente en un marco de ventana, el objeto se inicializa con sus datos mediante una llamada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.LoadDocData%2A>.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [Abrir y guardar elementos de proyecto](../extensibility/internals/opening-and-saving-project-items.md)   
 [Cómo: Abrir editores específicos del proyecto](../extensibility/how-to-open-project-specific-editors.md)   
 [Cómo: Abrir editores para documentos abiertos](../extensibility/how-to-open-editors-for-open-documents.md)   
 [Visualización de archivos mediante el comando Abrir archivo](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)
