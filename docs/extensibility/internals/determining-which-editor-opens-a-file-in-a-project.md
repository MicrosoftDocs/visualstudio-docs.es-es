---
title: Determinar qué editor abre un archivo en un proyecto ? Microsoft Docs
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af7037a3b4bfbae1801e802256af240d017d2789
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708657"
---
# <a name="determine-which-editor-opens-a-file-in-a-project"></a>Determinar qué editor abre un archivo en un proyecto
Cuando un usuario abre un archivo en un proyecto, el entorno pasa por un proceso de sondeo, abriendo finalmente el editor o diseñador adecuado para ese archivo. El procedimiento inicial empleado por el entorno es el mismo para los editores estándar y personalizados. El entorno utiliza una variedad de criterios al sondear qué editor usar para abrir un archivo y el VSPackage debe coordinar con el entorno durante este proceso.

 Por ejemplo, cuando un usuario selecciona el comando **Abrir** en el menú **Archivo** y, a continuación, elige *filename.rtf* (o cualquier otro archivo con una extensión *.rtf),* el entorno llama a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> implementación de cada proyecto, y finalmente recorre todas las instancias de proyecto de la solución. Los proyectos devuelven un conjunto de indicadores que identifican las notificaciones en un documento por prioridad. Con la prioridad más alta, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> el entorno llama al método adecuado. Para obtener más información sobre el proceso de sondeo, vea Agregar plantillas de elemento de [proyecto y proyecto.](../../extensibility/internals/adding-project-and-project-item-templates.md)

 El proyecto Archivos varios reclama todos los archivos que no son reclamados por otros proyectos. De esta manera, los editores personalizados pueden abrir documentos antes de que los editores estándar los abran. Si un proyecto de archivos varios reclama <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> un archivo, el entorno llama al método para abrir el archivo con un editor estándar. El entorno comprueba su lista interna de editores registrados en busca de uno que controle los archivos *.rtf.* Esta lista se encuentra en el registro en la siguiente clave:

 **HKEY_LOCAL_MACHINE, Software, Microsoft,\\\<VisualStudio versión> editor\\\<editor de la fábrica guía>-Extensiones**

 El entorno también comprueba los identificadores de clase de la **clave HKEY_CLASSES_ROOT-CLSID** para los objetos que tienen una subclave **DocObject**. Si la extensión de archivo se encuentra allí, una versión incrustada de la aplicación, como Microsoft Word, se crea in situ en Visual Studio. Estos objetos de documento deben <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage> ser archivos compuestos <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> que implementan la interfaz, o el objeto debe implementar la interfaz.

 Si no hay ningún generador de editores para los archivos *.rtf* en el registro, el entorno busca en la **HKEY_CLASSES_ROOT\\** clave .rtf y abre el editor especificado allí. Si la extensión de archivo no se encuentra en **HKEY_CLASSES_ROOT**, el entorno usa el editor de texto principal de Visual Studio para abrir el archivo, si se trata de un archivo de texto.

 Si se produce un error en el editor de texto principal, que se produce si el archivo no es un archivo de texto, el entorno utiliza su editor binario para el archivo.

 Si el entorno encuentra un editor para la extensión *.rtf* en su registro, carga el VSPackage que implementa este generador de editores. El entorno <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> llama al método en el nuevo VSPackage. El VSPackage `QueryService` `SID_SVsRegistorEditor`llama a <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> , mediante el método para registrar el generador del editor con el entorno.

 El entorno ahora vuelve a comprobar su lista interna de editores registrados para encontrar el generador de editores recién registrado para los archivos *.rtf.* El entorno llama a <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> la implementación del método, pasando el nombre de archivo y el tipo de vista que se desea crear.

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>
- <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>
