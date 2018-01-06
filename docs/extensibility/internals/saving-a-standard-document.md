---
title: "Guardar un documento estándar | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], saving standard documents
- projects [Visual Studio SDK], saving standard documents
- persistence, saving standard documents
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0cdfb4631420f6803e6434bd67b93bd713cfd1f7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="saving-a-standard-document"></a>Guardar un documento estándar
El entorno controla el guardar, guardar como y guardar todos los comandos. Cuando un usuario selecciona **guardar**, **Guardar como**, o **guardar todo** desde el **archivo** menú o se cierra la solución, lo que produce una  **Guardar todo**, se produce el siguiente proceso.  
  
 ![Editor estándar](../../extensibility/internals/media/public.gif "público")  
Guardar, guardar como y guardar todos los comandos de control para un editor estándar  
  
 Este proceso se detalla en los pasos siguientes:  
  
1.  Cuando el **guardar** y **Guardar como** comandos están seleccionados, el entorno utiliza el <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> del servicio para determinar la ventana de documento activo y, por tanto, deben guardarse el qué elementos. Una vez que se conozca la ventana de documento activo, el entorno busca el puntero de la jerarquía y el identificador (ID) del elemento del documento en la tabla document ejecución. Para obtener más información, consulte [ejecutando tabla Document](../../extensibility/internals/running-document-table.md).  
  
     Cuando el **guardar todo** comando está activado, el entorno utiliza la información de la tabla document ejecución para compilar la lista de todos los elementos que desee guardar.  
  
2.  Cuando la solución recibe un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> llamada, se recorre en iteración el conjunto de elementos seleccionados (es decir, las selecciones múltiples expuestas por el <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> servicio).  
  
3.  En cada elemento de la selección, la solución utiliza el puntero de la jerarquía para llamar a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> método para determinar si la **guardar** debe habilitarse el comando de menú. Si uno o varios elementos están desfasados, la **guardar** comando está habilitado. Si la jerarquía usa un editor estándar, los delegados de jerarquía consultar desfasadas estado al editor mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> método.  
  
4.  En cada elemento seleccionado que está dañada, la solución utiliza el puntero de la jerarquía para llamar a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> método en las jerarquías adecuadas.  
  
     Es común para la jerarquía para utilizar un editor estándar para editar el documento. En este caso, los datos del documento de objeto para ese editor debe admitir la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> interfaz. Una vez recibida la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> llamada al método, el proyecto debe informar el editor que se guarda el documento mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A> método en el objeto de datos del documento. El editor puede permitir que el entorno controlar la **Guardar como** cuadro de diálogo, mediante una llamada a `Query Service` para el <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> interfaz. Esto devuelve un puntero a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interfaz. El editor, a continuación, debe llamar a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> método, se pasa un puntero para el editor <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> implementación por medio de la `pPersistFile` parámetro. El entorno, a continuación, realiza la operación de guardar y proporciona el **Guardar como** cuadro de diálogo del Editor. El entorno, a continuación, llama de nuevo al editor con <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>.  
  
5.  Si el usuario está intentando guardar un documento sin título (es decir, un documento previamente que no haya guardado), realmente se realiza un comando Guardar como.  
  
6.  Para el comando Guardar como, el entorno muestra el cuadro de diálogo Guardar como, pedir al usuario un nombre de archivo.  
  
     Si ha cambiado el nombre del archivo, la jerarquía es responsable de actualizar el marco de documento información almacenada en caché mediante una llamada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A>(VSFPROPID_MkDocument).  
  
 Si el **Guardar como** comando mueve la ubicación del documento y la jerarquía es sensible a la ubicación del documento y, a continuación, la jerarquía es responsable de entregar la propiedad de la ventana de documento a otra jerarquía. Por ejemplo, esto ocurre si el proyecto hace un seguimiento si el archivo es un archivo interno o externo (archivos varios) en relación con el proyecto. Utilice el procedimiento siguiente para cambiar el propietario de un archivo al proyecto archivos varios.  
  
## <a name="changing-file-ownership"></a>Cambiar la propiedad de los archivos  
  
#### <a name="to-change-file-ownership-to-the-miscellaneous-files-project"></a>Para cambiar la propiedad de los archivos al proyecto archivos varios  
  
1.  Consultar el servicio para el <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager> interfaz.  
  
     Un puntero a <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2> se devuelve.  
  
2.  Llame a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> (`pszMkDocumentNew`, `punkWindowFrame`) método para transferir el documento a la nueva jerarquía. La jerarquía de la ejecución del comando Guardar como llama a este método.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Apertura y guardado de elementos de proyecto](../../extensibility/internals/opening-and-saving-project-items.md)