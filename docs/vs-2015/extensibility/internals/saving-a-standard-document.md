---
title: Guardar un documento estándar | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], saving standard documents
- projects [Visual Studio SDK], saving standard documents
- persistence, saving standard documents
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5040070287db6486fa62c9010fe023be31b04cbe
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68198085"
---
# <a name="saving-a-standard-document"></a>Guardado de un documento estándar
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

El entorno controla los guardar, guardar como y guardar todos los comandos. Cuando un usuario selecciona **guardar**, **Guardar como**, o **guardar todo** desde el **archivo** menú o se cierra la solución, lo que resulta en un  **Guardar todo**, se produce el siguiente proceso.  
  
 ![Editor estándar](../../extensibility/internals/media/public.gif "pública")  
Guardar, guardar como y guardar todos los comandos de control para un editor estándar  
  
 Este proceso se detalla en los pasos siguientes:  
  
1. Cuando el **guardar** y **Guardar como** comandos están seleccionados, el entorno utiliza el <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> de servicio para determinar la ventana de documento activo y, por tanto, se deben guardar qué elementos. Una vez que se conoce la ventana de documento activo, el entorno busca el puntero de la jerarquía y el identificador (ID) del elemento para el documento en la tabla de documentos en ejecución. Para obtener más información, consulte [tabla de documentos en ejecución](../../extensibility/internals/running-document-table.md).  
  
    Cuando el **guardar todo** comando está activado, el entorno usa la información de la tabla de documentos en ejecución para compilar la lista de todos los elementos para guardar.  
  
2. Cuando la solución recibe un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> llamada, recorre en iteración el conjunto de elementos seleccionados (es decir, las selecciones múltiples expuestas por el <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> service).  
  
3. En cada elemento de la selección, la solución utiliza el puntero de la jerarquía para llamar a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> método para determinar si el **guardar** debe habilitarse el comando de menú. Si uno o varios elementos están desfasados, la **guardar** comando está habilitado. Si la jerarquía usa un editor estándar, los delegados de la jerarquía consultar dirty estado en el editor mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> método.  
  
4. En cada elemento seleccionado que está desfasado, la solución utiliza el puntero de la jerarquía para llamar a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> método en las jerarquías adecuadas.  
  
    Es común para la jerarquía para utilizar un editor estándar para editar el documento. En este caso, los datos del documento objeto de ese editor debe admitir la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> interfaz. Una vez recibida la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> llamada al método, el proyecto debe informar el editor que se va a guardar el documento mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A> método en el objeto de datos. El editor puede permitir que el entorno para controlar la **Guardar como** cuadro de diálogo, mediante una llamada a `Query Service` para el <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> interfaz. Esto devuelve un puntero a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interfaz. El editor, a continuación, debe llamar a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> método y pasa un puntero para el editor <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> implementación por medio de la `pPersistFile` parámetro. El entorno, a continuación, realiza la operación de guardar y proporciona el **Guardar como** cuadro de diálogo del Editor. El entorno llama, a continuación, vuelva al editor con <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>.  
  
5. Si el usuario está intentando guardar un documento sin título (es decir, un documento no guardado anteriormente), realmente se realiza un comando Guardar como.  
  
6. El comando Guardar como, el entorno muestra el cuadro de diálogo Guardar como, preguntar al usuario un nombre de archivo.  
  
    Si ha cambiado el nombre del archivo, la jerarquía es responsable de actualizar el marco de documento información almacenada en caché mediante una llamada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A>(VSFPROPID_MkDocument).  
  
   Si el **Guardar como** comando mueve la ubicación del documento y la jerarquía es sensible a la ubicación del documento y, a continuación, la jerarquía es responsable de entregar la propiedad de la ventana de documento a otra jerarquía. Por ejemplo, esto se produce si el proyecto controla si el archivo es un archivo externo o interno (archivos varios) en relación con el proyecto. Utilice el procedimiento siguiente para cambiar la propiedad de un archivo al proyecto archivos varios.  
  
## <a name="changing-file-ownership"></a>Cambiar la propiedad de archivo  
  
#### <a name="to-change-file-ownership-to-the-miscellaneous-files-project"></a>Para cambiar la propiedad de archivo al proyecto archivos varios  
  
1. Consultar el servicio para el <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager> interfaz.  
  
     Un puntero a <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2> se devuelve.  
  
2. Llame a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> (`pszMkDocumentNew`, `punkWindowFrame`) método para transferir el documento a la nueva jerarquía. Este método llama a la jerarquía de la ejecución del comando Guardar como.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Apertura y guardado de elementos de proyecto](../../extensibility/internals/opening-and-saving-project-items.md)
