---
title: Guardar un documento personalizado | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- persistence, saving custom documents
- projects [Visual Studio SDK], saving custom documents
- editors [Visual Studio SDK], saving custom documents
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5425a1c35816fd85847915029e3b6f2da1ed75a6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132553"
---
# <a name="saving-a-custom-document"></a>Guardar un documento personalizado
Los identificadores de entorno la **guardar**, **Guardar como**, y **guardar todo** comandos. Cuando un usuario hace clic en **guardar**, **Guardar como**, **o guardar todo** en el **archivo** menú o se cierra la solución, lo que genera un comando Guardar todo, lo siguiente se produce el proceso.  
  
 ![Guardar Editor de clientes](../../extensibility/internals/media/private.gif "privada")  
Guardar, guardar como y guardar todos los comandos de control para un editor personalizado  
  
 Este proceso se detalla en los pasos siguientes:  
  
1.  Para el **guardar** y **Guardar como** comandos, el entorno utiliza el <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> del servicio para determinar la ventana de documento activo y, por tanto, deben guardarse el qué elementos. Una vez que se conozca la ventana de documento activo, el entorno busca el puntero de la jerarquía y el identificador (ID) del elemento del documento en la tabla document ejecución. Para obtener más información, consulte [ejecutando tabla Document](../../extensibility/internals/running-document-table.md).  
  
     Para el comando Guardar todo, el entorno utiliza la información en la tabla de documento de ejecución para compilar la lista de todos los elementos que desee guardar.  
  
2.  Cuando la solución recibe un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> llamada, se recorre en iteración el conjunto de elementos seleccionados (es decir, las selecciones múltiples expuestas por el <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> servicio).  
  
3.  En cada elemento de la selección, la solución utiliza el puntero de la jerarquía para llamar a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> método para determinar si se debe habilitar el comando de menú de guardar. Si uno o más elementos son desfasados, se habilita el comando Guardar. Si la jerarquía usa un editor estándar, los delegados de jerarquía consultar desfasadas estado al editor mediante una llamada a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> método.  
  
4.  En cada elemento seleccionado que está dañada, la solución utiliza el puntero de la jerarquía para llamar a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> método en las jerarquías adecuadas.  
  
     En el caso de un editor personalizado, la comunicación entre el objeto de datos de documento y el proyecto es privada. Por lo tanto, cualquier problema de persistencia especiales se administra entre estos dos objetos.  
  
    > [!NOTE]
    >  Si implementa su propia persistencia, asegúrese de llamar a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> método ahorrar tiempo. Este método comprueba para asegurarse de que es seguro guardar el archivo (por ejemplo, el archivo no es de solo lectura).  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Apertura y guardado de elementos de proyecto](../../extensibility/internals/opening-and-saving-project-items.md)