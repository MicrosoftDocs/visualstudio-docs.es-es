---
title: Determinar qué Editor abre un archivo en un proyecto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], determining which editor opens a file
- projects [Visual Studio SDK], determining which editor opens file
- project types, determining which editor opens a file
- persistence, determining which editor opens a file
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b61aa726a7088d08db6d759a9835816dcaf826a7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53941065"
---
# <a name="determine-which-editor-opens-a-file-in-a-project"></a>Determinar qué editor abre un archivo en un proyecto
Cuando un usuario abre un archivo en un proyecto, el entorno pasa por un proceso de sondeo, finalmente, abrir el editor adecuado o el diseñador para ese archivo. El procedimiento inicial empleado por el entorno es el mismo para los editores estándar y personalizados. El entorno usa una variedad de criterios al sondear el editor que desea utilizar para abrir un archivo y el VSPackage debe coordinarse con el entorno durante este proceso.  
  
 Por ejemplo, cuando un usuario selecciona el **abierto** comando desde el **archivo** menú y, a continuación, elige *filename.rtf* (o cualquier otro archivo con un *.rtf*extensión), el entorno llama a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> implementación para cada proyecto, finalmente, recorrer todas las instancias de proyecto en la solución. Los proyectos de devuelven un conjunto de marcas que identifican las notificaciones en un documento por prioridad. Con la prioridad más alta, el entorno llama a la correspondiente <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> método. Para obtener más información sobre el proceso de sondeo, consulte [Agregar proyecto y plantillas de elemento de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
 El proyecto archivos varios de notificaciones de todos los archivos que no son reclamados por otros proyectos. De este modo, los editores personalizados pueden abrir documentos antes de abrirlos de editores estándar. Si un archivo de notificaciones de un proyecto de archivos varios, el entorno llama a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> método para abrir el archivo con un editor estándar. El entorno examina su lista interna de los editores registrados para aquel que administra *.rtf* archivos. Esta lista se encuentra en el registro en la siguiente clave:  
  
 **HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\\<versión > \Editors\\\<guid del generador de editores > \Extensions**
  
 El entorno también comprueba los identificadores de clase el **HKEY_CLASSES_ROOT\CLSID** clave para los objetos que tengan una subclave **DocObject**. Si la extensión de archivo se encuentra allí, una versión incrustada de la aplicación, como Microsoft Word, se crea en el lugar en Visual Studio. Estos objetos de documento deben ser archivos compuestos que implementan la <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage> interfaz o el objeto debe implementar la <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> interfaz.  
  
 Si no hay ningún generador de editores para *.rtf* archivos en el registro, a continuación, busca el entorno en el **HKEY_CLASSES_ROOT\\.rtf** clave y se abre el editor especificado no existe. Si la extensión de archivo no se encuentra en **HKEY_CLASSES_ROOT**, a continuación, el entorno usa el editor de texto básico de Visual Studio para abrir el archivo, si es un archivo de texto.  
  
 Si se produce un error en el editor de texto básico, que se produce que si el archivo no es un archivo de texto, el entorno usa su editor binario para el archivo.  
  
 Si el entorno de encontrar un editor para el *.rtf* extensión en su registro, carga el VSPackage que implemente este generador de editores. El entorno llama a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> método en el nuevo VSPackage. Las llamadas de VSPackage `QueryService` para `SID_SVsRegistorEditor`, usando la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> método para registrar el generador de editores con el entorno.  
  
 El entorno reexamina ahora su lista interna de los editores registrados para encontrar el generador de editores recién registrado para *.rtf* archivos. El entorno llama a la implementación de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> método, pasando el tipo de nombre y la vista de archivo para crear.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>   
 <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>