---
title: Crear instancias del editor principal mediante la API heredada | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - instantiating editor
ms.assetid: dda23b18-96ef-43c6-b0dc-06d15cbe5cbb
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 29306a16390039c8ee6e424b81a5ff617e533ab4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203907"
---
# <a name="instantiating-the-core-editor-by-using-the-legacy-api"></a>Creación de instancias del editor principal mediante la API heredada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El editor es responsable de las funciones de edición de texto, como inserción, eliminación, copia y pegado. Combina estas funciones con las proporcionadas por los servicios de lenguaje, como el color de texto, la sangría y la finalización de instrucciones de IntelliSense.  
  
 Puede crear instancias de una instancia del editor principal de tres maneras:  
  
- Cree explícitamente una instancia del editor principal en una ventana.  
  
- Proporcionar un generador de editores que devuelva una instancia del editor principal  
  
- Abra un archivo de la jerarquía del proyecto.  
  
  En las secciones siguientes se describe cómo usar la API heredada para crear una instancia del editor.  
  
## <a name="explicitly-opening-a-core-editor-instance"></a>Abrir explícitamente una instancia de editor principal  
 Cuando se obtiene explícitamente una instancia del editor principal:  
  
- Obtiene un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> para contener el objeto de datos del documento que se está editando.  
  
- Cree una representación orientada a líneas del objeto de datos del documento mediante <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> la creación de una interfaz desde la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interfaz.  
  
- Se establece <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> como el objeto de datos de documento para una instancia de la implementación predeterminada de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> interfaz, mediante el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetBuffer%2A> método.  
  
   Hospede la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> instancia en una <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> interfaz mediante el <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateToolWindow%2A> método.  
  
  En este punto, la visualización de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> interfaz proporciona una ventana que contiene una instancia del editor básico.  
  
  Sin embargo, esto no es una instancia muy útil, ya que no tiene teclas de método abreviado o acceso a características avanzadas. Para obtener acceso a las teclas de método abreviado y a las características avanzadas:  
  
- Utilice el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> método para asociar un servicio de lenguaje y el objeto de datos de documento que utiliza el editor.  
  
- Cree sus propias teclas de método abreviado o use el valor predeterminado del sistema estableciendo las propiedades de presentación de los <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> objetos. Para ello, llame al <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetGuidProperty%2A> método con la <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> propiedad.  
  
   Para obtener y usar teclas de método abreviado no estándar, debe generarlas mediante el archivo. Vsct. Para obtener más información, consulta [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="how-to-use-an-editor-factory-to-obtain-the-core-editor"></a>Cómo usar un generador de editores para obtener el editor básico  
 Al implementar un editor principal con un generador de editores mediante el <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> método, siga todos los pasos descritos en la sección anterior para hospedar explícitamente un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> objeto con un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> objeto de datos de documento, en un <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> objeto.  
  
 Para mostrar el texto, obtenga una <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaz del <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> objeto y llame al <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> método.  
  
 Para proporcionar un servicio de lenguaje al editor, llame al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> método en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> método.  
  
 Para obtener las teclas de método abreviado predeterminadas, a diferencia de la sección anterior, se usa el contexto de comando devuelto por el <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> método al obtener el editor básico desde el <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> método.  
  
 Si el <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> método devuelve el mismo GUID de comando que el editor de texto, la instancia del editor principal obtiene automáticamente las teclas de método abreviado predeterminadas.  
  
 Para obtener información general, vea [Tutorial: crear un editor principal y registrar un tipo de archivo del editor](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md).  
  
## <a name="see-also"></a>Consulte también  
 [Dentro del editor principal](../extensibility/inside-the-core-editor.md)   
 [Abrir y guardar elementos de proyecto](../extensibility/internals/opening-and-saving-project-items.md)   
 [Tutorial: Crear un editor principal y registrar un tipo de archivo del editor](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)
