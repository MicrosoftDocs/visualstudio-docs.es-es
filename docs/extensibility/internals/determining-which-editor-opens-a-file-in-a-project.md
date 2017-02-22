---
title: "Determinar qu&#233; Editor se abre un archivo en un proyecto | Microsoft Docs"
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
  - "editores [Visual Studio SDK], determinar qué editor abre un archivo"
  - "proyectos [Visual Studio SDK], determinar qué editor abre el archivo"
  - "tipos de proyecto, determinar qué editor abre un archivo"
  - "persistencia, determinar qué editor abre un archivo"
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Determinar qu&#233; Editor se abre un archivo en un proyecto
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cuando un usuario abre un archivo en un proyecto, el entorno pasa por el editor correspondiente o un diseñador de sondeo de un proceso, finalmente sin abrir para ese archivo.  El procedimiento inicial empleado por el entorno es el mismo para la norma y editores personalizados.  El entorno utiliza diversos criterios a sondear que el editor que desea utilizar para abrir un archivo y el paquete VSPackage debe coordinarse con el entorno durante este proceso.  
  
 Por ejemplo, cuando un usuario selecciona el comando de **Abrir** de menú de **Archivo** , y elija `filename`.rtf \(o cualquier otro archivo con una extensión .rtf\), el entorno la implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> para cada proyecto, al completar un ciclo finalmente con todas las instancias del proyecto en la solución.  Los proyectos devuelven un conjunto de marcas que identifican peticiones en un documento por prioridad.  Mediante la prioridad máxima, el entorno llama al método adecuado de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> .  Para obtener más información sobre el proceso de sondeo, [Agregar proyecto y plantillas de elemento de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
 El proyecto de archivos varios petición todos los archivos que no son demandados por otros proyectos.  De esta manera, editores personalizados puede documentos abiertos antes de abrir los editores estándar ellos.  Si un proyecto de archivos varios petición un archivo, el entorno llama al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> para abrir el archivo con un editor estándar.  El entorno comprueba su lista de editores registrados para uno que controle los archivos .rtf.  Esta lista se encuentra en el registro de la siguiente clave:  
  
 \[HKEY\_LOCAL\_MACHINE \\Software\\Microsoft\\VisualStudio\\\<`versión`\> \\Editors\\{\<`guid del generador del editor`\>} \\Extensions\]  
  
 el entorno también comprueba los identificadores de clase en el HKEY\_CLASSES\_ROOT \\CLSID key for any objects that have a sub\-key DocObject.  Si la extensión de archivo se encuentra allí, una versión incrustada de la aplicación, como Microsoft Word, en contexto creado en Visual Studio.  Estos objetos document deben ser archivos compuestos que implementan la interfaz de <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage> , o el objeto debe implementar la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> .  
  
 Si no hay ningún generador de editor para los archivos .rtf del registro, el entorno busca en la clave de HKEY\_CLASSES\_ROOT \\ .rtf y abra el editor especificado allí.  Si la extensión de archivo no se encuentra en HKEY\_CLASSES\_ROOT, el entorno utiliza el editor de texto básico de Visual Studio para abrir el archivo si es un archivo de texto.  
  
 Si el editor de texto básico, que aparece si el archivo no es un archivo de texto, el entorno usa el editor binario para el archivo.  
  
 Si el entorno encuentra un editor para la extensión .rtf del registro, carga el Paquete que implementa esta generador del editor.  El entorno llama al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> en el nuevo paquete VSPackage.  El Paquete llama a `QueryService` para `SID_SVsRegistorEditor`, utilizando el método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> para registrar el generador del editor con el entorno.  
  
 Ahora que el entorno vuelve a inspeccionar su lista de editores registrados para buscar el generador recién registrada de editor para los archivos .rtf.  El entorno llama a la implementación del método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> , pasando el tipo de nombre de archivo y de vista para crear.  
  
## Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>   
 <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>