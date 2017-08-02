---
title: "Guardar un documento est&#225;ndar | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editores [Visual Studio SDK], guardar documentos estándares"
  - "proyectos [Visual Studio SDK], guardar documentos estándares"
  - "persistencia, guardar documentos estándares"
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Guardar un documento est&#225;ndar
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

El entorno administra el Guardar, Guardar como, y los comandos de Guardar Todo.  Cuando un usuario selecciona **Guardar**, **Guardar como**, o **Guardar todos** de menú de **Archivo** o cierre la solución, por lo que **Guardar todos**, el proceso siguiente aparece.  
  
 ![Editor estándar](~/extensibility/internals/media/public.gif "Public")  
Guarde, Guardar como, y un comando de Guardar Todo que administra para un editor estándar  
  
 este proceso se detalla en los pasos siguientes:  
  
1.  Cuando los comandos de **Guardar** y de **Guardar como** son seleccionado, el entorno utiliza el servicio de <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> para determinar la ventana de documento activo y así qué elementos deben guardarse.  Una vez que se conoce la ventana de documento activo, el entorno encuentra el identificador del puntero y el elemento de la jerarquía \(itemID\) para el documento en la tabla en el documento.  Para obtener más información, vea [Tabla de documentos de ejecución](../../extensibility/internals/running-document-table.md).  
  
     Cuando el comando de **Guardar todos** está seleccionado, el entorno utiliza la información de la tabla actual del documento para compilar la lista de todos los elementos para guardar.  
  
2.  Cuando la solución recibe una llamada de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> , recorre en iteración el conjunto de elementos seleccionados \(es decir, las selecciones múltiples expuestas por el servicio de <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> \).  
  
3.  En cada elemento en la selección, la solución utiliza el puntero de la jerarquía para llamar al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> para determinar si el comando de menú **Save** debe estar habilitado.  Si uno o más elementos son modificados, después habilitan el comando de **Save** .  Si la jerarquía usa un editor estándar, la jerarquía delega consultar el estado modificado el editor llamando al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> .  
  
4.  En cada elemento seleccionado que sea modificado, la solución utiliza el puntero de la jerarquía para llamar al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> en las jerarquías adecuadas.  
  
     Es habitual que la jerarquía utilice un editor estándar para modificar el documento.  En este caso, el objeto del documento para ese editor debe admitir la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> .  Al recibir la llamada al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> , el proyecto debe informar al editor que el documento se está guardado llamando al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A> en el objeto del documento.  El editor puede permitir que el entorno controle el cuadro de diálogo de **Guardar como** , llamando a `Query Service` para la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> .  esto devuelve un puntero a la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> .  El editor debe llamar al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> , pasar un puntero a la implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> de editor mediante el parámetro de `pPersistFile` .  El entorno realice la operación de Guardar y proporciona el cuadro de diálogo de **Guardar como** para el editor.  Las llamadas del entorno vuelve a editor con <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>.  
  
5.  Si el usuario intenta guardar un documento sin título \(es decir, un documento previamente no guardados\), un comando guardar como para se realiza realmente.  
  
6.  Para el comando guardar como para, el entorno muestra el cuadro de diálogo Guardar como, solicitando al usuario un nombre de archivo.  
  
     Si el nombre del archivo se ha modificado, la jerarquía es responsable de actualizar la información almacenada en la caché de marco de documento llamando a <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A>\(VSFPROPID\_MkDocument\).  
  
 Si el comando de **Guardar como** mueve la ubicación del documento, y la jerarquía es sensible a ubicaciones de documentos, la jerarquía es responsable de dar de la propiedad de la ventana de documento abierto en otra jerarquía.  Por ejemplo, esto ocurre si el proyecto controla si el archivo es un interno o un archivo externo \(archivos varios\) en relación con el proyecto.  Utilice el siguiente procedimiento para cambiar la propiedad de un archivo al proyecto de archivos varios.  
  
## Cambiar la propiedad de archivo  
  
#### A la propiedad del archivo de cambios en el proyecto de archivos varios  
  
1.  consulta Service para la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager> .  
  
     un puntero a <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2> se devuelve.  
  
2.  Llame al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> \(`pszMkDocumentNew`, `punkWindowFrame`\) para transferir el documento a la nueva jerarquía.  La jerarquía que realiza el comando guardar como para llama a este método.  
  
## Vea también  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Abrir y guardar elementos de proyecto](../../extensibility/internals/opening-and-saving-project-items.md)