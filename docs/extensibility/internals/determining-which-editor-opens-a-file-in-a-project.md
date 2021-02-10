---
title: Determinar qué editor abre un archivo en un proyecto | Microsoft Docs
description: Obtenga información sobre las claves del registro y los métodos del SDK de Visual Studio que usa Visual Studio para determinar qué editor abre un archivo en un proyecto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], determining which editor opens a file
- projects [Visual Studio SDK], determining which editor opens file
- project types, determining which editor opens a file
- persistence, determining which editor opens a file
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 48d642c8a3b7883507c06453c0025badc299ce75
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963424"
---
# <a name="determine-which-editor-opens-a-file-in-a-project"></a>Determinar qué editor abre un archivo en un proyecto
Cuando un usuario abre un archivo en un proyecto, el entorno pasa por un proceso de sondeo y, finalmente, abre el editor o el diseñador adecuado para ese archivo. El procedimiento inicial empleado por el entorno es el mismo para los editores estándar y personalizados. El entorno utiliza diversos criterios al sondear qué editor se va a usar para abrir un archivo y el VSPackage debe coordinarse con el entorno durante este proceso.

 Por ejemplo, cuando un usuario selecciona el comando **abrir** en el menú **archivo** y, a continuación, elige *filename. rtf* (o cualquier otro archivo con la extensión *. rtf* ), el entorno llama a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> implementación de cada proyecto y, finalmente, recorre todas las instancias del proyecto en la solución. Los proyectos devuelven un conjunto de marcas que identifican las notificaciones en un documento por prioridad. Con la prioridad más alta, el entorno llama al <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> método adecuado. Para obtener más información sobre el proceso de sondeo, vea [agregar plantillas de proyecto y de elemento de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md).

 El proyecto de archivos varios reclama todos los archivos que no se reclaman en otros proyectos. De esta manera, los editores personalizados pueden abrir documentos antes de que los editores estándar los abran. Si un proyecto de archivos varios reclama un archivo, el entorno llama al <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> método para abrir el archivo con un editor estándar. El entorno comprueba la lista interna de editores registrados de una que controla los archivos *. rtf* . Esta lista se encuentra en el registro en la siguiente clave:

 **HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\ \<version> \Editors \\ \<editor factory guid> \Extensions**

 El entorno comprueba también los identificadores de clase en la clave **HKEY_CLASSES_ROOT\CLSID** para los objetos que tienen una subclave **DocObject**. Si se encuentra la extensión de archivo, se crea una versión incrustada de la aplicación, como Microsoft Word, en el contexto de Visual Studio. Estos objetos de documento deben ser archivos compuestos que implementen la <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage> interfaz o el objeto debe implementar la <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> interfaz.

 Si no hay ningún generador de editores para los archivos *. rtf* en el registro, el entorno busca en la clave **HKEY_CLASSES_ROOT \\ . rtf** y abre el editor especificado allí. Si no se encuentra la extensión de archivo en **HKEY_CLASSES_ROOT**, el entorno usa el editor de texto principal de Visual Studio para abrir el archivo, si es un archivo de texto.

 Si se produce un error en el editor de texto principal, que se produce si el archivo no es un archivo de texto, el entorno utiliza su editor binario para el archivo.

 Si el entorno encuentra un editor para la extensión *. rtf* en su registro, carga el VSPackage que implementa este generador de editores. El entorno llama al <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> método en el VSPackage nuevo. El VSPackage llama a `QueryService` para `SID_SVsRegistorEditor` , utilizando el <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> método para registrar el generador de editores en el entorno.

 Ahora, el entorno comprueba la lista interna de editores registrados para encontrar el generador del editor recién registrado para los archivos *. rtf* . El entorno llama a la implementación del <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> método, pasando el nombre de archivo y el tipo de vista que se van a crear.

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>
- <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>
