---
title: "Determinar qué Editor abre un archivo en un proyecto | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], determining which editor opens a file
- projects [Visual Studio SDK], determining which editor opens file
- project types, determining which editor opens a file
- persistence, determining which editor opens a file
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f7c69bc08d0f1bb72a37b76fca2d402d73036deb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="determining-which-editor-opens-a-file-in-a-project"></a>Determinar qué Editor se abre un archivo en un proyecto
Cuando un usuario abre un archivo en un proyecto, el entorno pasa por un proceso de sondeo, puede abrir el editor correspondiente o el diseñador para ese archivo. El procedimiento inicial empleado por el entorno es el mismo para los editores estándar y personalizados. El entorno utiliza una variedad de criterios al sondear el editor que desea utilizar para abrir un archivo y el VSPackage debe coordinar con el entorno durante este proceso.  
  
 Por ejemplo, cuando un usuario selecciona el **abiertos** línea de comandos desde el **archivo** menú y, a continuación, elige `filename`.rtf (o cualquier otro archivo con la extensión .rtf), el entorno llama el <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> implementación para cada proyecto, puede recorrer todas las instancias de proyecto en la solución. Proyectos de devuelven un conjunto de marcas que identifican las notificaciones en un documento por prioridad. Con la prioridad más alta, el entorno llama a la correspondiente <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> método. Para obtener más información sobre el proceso de sondeo, [Agregar proyecto y plantillas de elementos de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
 El proyecto archivos varios notificaciones de todos los archivos que no son reclamados por otros proyectos. De esta manera, editores personalizados pueden abrir documentos antes de abran de editores estándares. Si un archivo de notificaciones de un proyecto de archivos varios, el entorno llama a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> método para abrir el archivo con un editor estándar. El entorno comprueba su lista interna de editores registrados por uno que se controla .rtf (archivos). Esta lista se encuentra en el registro en la siguiente clave:  
  
 [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<`version`> \Editors\\{<`editor factory guid`>} \Extensions]  
  
 El entorno también comprueba los identificadores de clase en la clave HKEY_CLASSES_ROOT\CLSID para los objetos que tienen una sub-clave DocObject. Si la extensión de archivo se encuentra allí, una versión incrustada de la aplicación, como Microsoft Word, se crea en lugar de Visual Studio. Estos objetos de documento deben ser archivos compuestos que implementan la <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage> interfaz o el objeto debe implementar la <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> interfaz.  
  
 Si no hay ningún generador del editor para .rtf (archivos) en el registro, el entorno busca en HKEY_CLASSES_ROOT \\clave .rtf y abre el editor especificado no existe. Si no se encuentra la extensión de archivo en HKEY_CLASSES_ROOT, el entorno usa el editor de texto principal de Visual Studio para abrir el archivo si es un archivo de texto.  
  
 Si se produce un error en el editor de texto básico, que se produce que si el archivo no es un archivo de texto, el entorno utiliza su editor binario para el archivo.  
  
 Si el entorno de encontrar un editor para la extensión .rtf en su registro, carga el VSPackage que implemente este generador de editores. El entorno llama el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> método en el nuevo paquete de VS. Las llamadas de VSPackage `QueryService` para `SID_SVsRegistorEditor`, usando la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> método para registrar el generador del editor con el entorno.  
  
 Ahora, el entorno vuelve a examina su lista interna de editores registrados para buscar el generador de editores recién registrado para .rtf (archivos). El entorno llama a la implementación de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> método, pasando el tipo de nombre y la vista de archivo para crear.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>   
 <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>