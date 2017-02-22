---
title: "Guardar un documento personalizado | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "persistencia, guardar documentos personalizados"
  - "proyectos [Visual Studio SDK], guardar documentos personalizados"
  - "editores [Visual Studio SDK], guardar documentos personalizados"
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Guardar un documento personalizado
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

El entorno controla **Save**, **Save As**, y los comandos de **Save All** .  Cuando un usuario hace clic en **Guardar**, **Guardar como**, **o Guardar Todo** en el menú de **Archivo** o cierre la solución, lo que da como resultado un Guardar Todo, el proceso siguiente aparece.  
  
 ![Guardar Editor de clientes](../../extensibility/internals/media/private.gif "Private")  
Guarde, Guardar como, y un comando de Guardar Todo que administra para un editor personalizado  
  
 este proceso se detalla en los pasos siguientes:  
  
1.  Para los comandos de **Guardar** y de **Guardar como** , el entorno utiliza el servicio de <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> para determinar la ventana de documento activo y así qué elementos deben guardarse.  Una vez que se conoce la ventana de documento activo, el entorno encuentra el identificador del puntero y el elemento de la jerarquía \(itemID\) para el documento en la tabla en el documento.  Para obtener más información, vea [Tabla de documentos de ejecución](../../extensibility/internals/running-document-table.md).  
  
     Para el comando de Guardar Todo, el entorno utiliza la información de la tabla actual del documento para compilar la lista de todos los elementos para guardar.  
  
2.  Cuando la solución recibe una llamada de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> , recorre en iteración el conjunto de elementos seleccionados \(es decir, las selecciones múltiples expuestas por el servicio de <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> \).  
  
3.  En cada elemento en la selección, la solución utiliza el puntero de la jerarquía para llamar al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> para determinar si el comando de menú Save debe estar habilitado.  Si uno o más elementos son modificados, después habilitan el comando Save.  Si la jerarquía usa un editor estándar, la jerarquía delega consultar el estado modificado el editor llamando al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> .  
  
4.  En cada elemento seleccionado que sea modificado, la solución utiliza el puntero de la jerarquía para llamar al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> en las jerarquías adecuadas.  
  
     En el caso de un editor personalizado, la comunicación entre el objeto del documento y el proyecto es privada.  Por tanto, cualquier problema especial de persistencia se controla entre estos dos objetos.  
  
    > [!NOTE]
    >  Si implementa posee la persistencia, asegúrese de llamar al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> para ahorrar tiempo.  Las comprobaciones de este método para asegurarse de que es seguro guardar el archivo \(por ejemplo, el archivo no son de sólo lectura\).  
  
## Vea también  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Abrir y guardar elementos de proyecto](../../extensibility/internals/opening-and-saving-project-items.md)