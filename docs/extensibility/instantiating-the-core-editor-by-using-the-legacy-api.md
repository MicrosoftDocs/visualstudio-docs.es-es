---
title: Crear una instancia el Editor básico mediante la API heredado | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - instantiating editor
ms.assetid: dda23b18-96ef-43c6-b0dc-06d15cbe5cbb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a720126324faf1ab9a9a4e07086bc4ec711508f6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="instantiating-the-core-editor-by-using-the-legacy-api"></a>Crear una instancia el Editor básico mediante la API heredado
El editor es responsable de las funciones como inserción, eliminación, copiar y pegar de edición de texto. Estas funciones combinan con los proporcionados por los servicios de lenguaje, como el color de texto, la sangría y la finalización de instrucciones de IntelliSense.  
  
 Puede crear una instancia del editor principal de una de estas tres maneras:  
  
-   Cree explícitamente una instancia del núcleo de editor en una ventana.  
  
-   Proporciona un generador de editores que devuelve una instancia del editor principal  
  
-   Abrir un archivo desde la jerarquía del proyecto.  
  
 Las secciones siguientes tratan cómo usar la API heredada para crear una instancia del editor.  
  
## <a name="explicitly-opening-a-core-editor-instance"></a>Abrir explícitamente una instancia del Editor de núcleo  
 Cuando se obtienen explícitamente una instancia del editor principal:  
  
-   Obtener un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> para contener el objeto de datos de documento que se está editando.  
  
-   Crear una representación de línea orientada a servicios del objeto de datos de documentos mediante la creación de un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> de la interfaz de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interfaz.  
  
-   Establecer <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> como el objeto de datos de documento para una instancia de la implementación predeterminada de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> interfaz, usando la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetBuffer%2A> método.  
  
     Host de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> de instancia de un <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> interfaz mediante el uso de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateToolWindow%2A> método.  
  
 En este momento, mostrar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> interfaz proporciona una ventana que contiene una instancia del editor principal.  
  
 Sin embargo, esto no es una instancia muy útil, porque no tienen teclas de método abreviado, o tener acceso a las funciones avanzadas. Para obtener acceso a las características avanzadas y teclas de método abreviado:  
  
-   Use la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> método para asociar un servicio de lenguaje y el objeto de datos de documento que usa el editor.  
  
-   Cree sus propias teclas de método abreviado, o usar el valor predeterminado del sistema estableciendo la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> objetos muestran propiedades. Para ello, llame a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetGuidProperty%2A> método con el <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> propiedad.  
  
     Para obtener y usar teclas de método abreviado no estándar, generarlos mediante el archivo .vsct. Para obtener más información, consulta [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="how-to-use-an-editor-factory-to-obtain-the-core-editor"></a>Cómo usar un generador del Editor para obtener el Editor básico  
 Al implementar un editor de núcleo con un generador del editor mediante el <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> método, siga todos los pasos que se describen en la sección anterior para hospedar explícitamente un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> con una <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> objeto de datos del documento, en un <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> objeto.  
  
 Para mostrar el texto, obtener una <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaz desde el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> objeto y llame al método el <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> método.  
  
 Para proporcionar un servicio de lenguaje para el editor, llame a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> método dentro de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> método.  
  
 Para obtener predeterminado teclas de método abreviado, a diferencia de la sección anterior, se usa el contexto de comandos devolviendo por la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> método al obtener el editor principal de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> método.  
  
 Si el <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> método devuelve el mismo GUID de comando como el editor de texto, la instancia del editor principal obtiene automáticamente el valor predeterminado teclas de método abreviado.  
  
 Para obtener información general, vea [Tutorial: crear un Editor de núcleo y registrar un tipo de archivo del Editor de](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md).  
  
## <a name="see-also"></a>Vea también  
 [Dentro del Editor de núcleo](../extensibility/inside-the-core-editor.md)   
 [Abrir y guardar elementos de proyecto](../extensibility/internals/opening-and-saving-project-items.md)   
 [Tutorial: Crear un Editor de núcleo y registrar un tipo de archivo del Editor](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)