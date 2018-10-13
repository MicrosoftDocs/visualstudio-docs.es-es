---
title: Determinar qué Editor abre un archivo en un proyecto | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], determining which editor opens a file
- projects [Visual Studio SDK], determining which editor opens file
- project types, determining which editor opens a file
- persistence, determining which editor opens a file
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ba2241a8c8572b46dab0d4df1776f65ab8f10d67
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49241038"
---
# <a name="determining-which-editor-opens-a-file-in-a-project"></a>Determinación del editor que abre un archivo en un proyecto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Cuando un usuario abre un archivo en un proyecto, el entorno pasa por un proceso de sondeo, finalmente, abrir el editor adecuado o el diseñador para ese archivo. El procedimiento inicial empleado por el entorno es el mismo para los editores estándar y personalizados. El entorno usa una variedad de criterios al sondear el editor que desea utilizar para abrir un archivo y el VSPackage debe coordinarse con el entorno durante este proceso.  
  
 Por ejemplo, cuando un usuario selecciona el **abierto** comando desde el **archivo** menú y, a continuación, elige `filename`.rtf (o cualquier otro archivo con una extensión .rtf), el entorno llama a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> implementación para cada proyecto, finalmente, recorrer todas las instancias de proyecto en la solución. Los proyectos de devuelven un conjunto de marcas que identifican las notificaciones en un documento por prioridad. Con la prioridad más alta, el entorno llama a la correspondiente <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> método. Para obtener más información sobre el proceso de sondeo, [Agregar proyecto y plantillas de elemento de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
 El proyecto archivos varios de notificaciones de todos los archivos que no son reclamados por otros proyectos. De este modo, los editores personalizados pueden abrir documentos antes de abrirlos de editores estándar. Si un archivo de notificaciones de un proyecto de archivos varios, el entorno llama a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> método para abrir el archivo con un editor estándar. El entorno examina su lista interna de los editores registrados para uno que controla los archivos .rtf. Esta lista se encuentra en el registro en la siguiente clave:  
  
 [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<`version`> \Editors\\{<`editor factory guid`>} \Extensions]  
  
 El entorno también comprueba los identificadores de clase en la clave HKEY_CLASSES_ROOT\CLSID para los objetos que tienen una subclave DocObject. Si la extensión de archivo se encuentra allí, una versión incrustada de la aplicación, como Microsoft Word, se crea en el lugar en Visual Studio. Estos objetos de documento deben ser archivos compuestos que implementan la <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage> interfaz o el objeto debe implementar la <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> interfaz.  
  
 Si no hay ningún generador de editores para los archivos .rtf del registro, el entorno busca en HKEY_CLASSES_ROOT \\.rtf clave y se abre el editor especificado no existe. Si no se encuentra la extensión de archivo en HKEY_CLASSES_ROOT, el entorno usa el editor de texto básico de Visual Studio para abrir el archivo si es un archivo de texto.  
  
 Si se produce un error en el editor de texto básico, que se produce que si el archivo no es un archivo de texto, el entorno usa su editor binario para el archivo.  
  
 Si el entorno de encontrar un editor para la extensión .rtf en su registro, carga el VSPackage que implemente este generador de editores. El entorno llama a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> método en el nuevo VSPackage. Las llamadas de VSPackage `QueryService` para `SID_SVsRegistorEditor`, usando la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> método para registrar el generador de editores con el entorno.  
  
 Ahora, el entorno de volver a examina su lista interna de editores registrados para encontrar el generador de editores recién registrado para .rtf (archivos). El entorno llama a la implementación de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> método, pasando el tipo de nombre y la vista de archivo para crear.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>   
 <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>

