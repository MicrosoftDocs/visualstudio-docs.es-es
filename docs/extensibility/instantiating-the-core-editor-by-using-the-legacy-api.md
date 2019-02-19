---
title: El Editor básico de creación de instancias mediante la API heredada | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - instantiating editor
ms.assetid: dda23b18-96ef-43c6-b0dc-06d15cbe5cbb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5fad305d97407995e15887848e3672e382ad54e5
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/18/2019
ms.locfileid: "56335563"
---
# <a name="instantiate-the-core-editor-by-using-the-legacy-api"></a>Crear una instancia el editor básico mediante la API heredada

El editor es responsable de las funciones como inserción, eliminación, copiar y pegar de edición de texto. Combina estas funciones con las funciones proporcionadas por los servicios de lenguaje, como el color de texto, sangría y finalización de instrucciones de IntelliSense.

Puede crear una instancia del editor de núcleo en uno de tres maneras:

- Crea explícitamente una instancia del núcleo del editor en una ventana.

- Proporciona un generador de editores que devuelve una instancia del editor de núcleo

- Abrir un archivo de la jerarquía del proyecto.

Las secciones siguientes describen cómo usar la API heredada para crear una instancia del editor.

## <a name="explicitly-open-a-core-editor-instance"></a>Abrir explícitamente una instancia del editor de núcleo

Al obtener explícitamente una instancia del editor de núcleo:

- Obtener un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> que contenga el objeto de datos de documento que se está editando.

- Crear una representación orientada a servicios de línea del objeto de datos de documento mediante la creación de un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> interfaz desde el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interfaz.

- Establecer <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> como el objeto de datos de una instancia de la implementación predeterminada de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> interfaz, mediante el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetBuffer%2A> método.

   Host del <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> de instancia en un <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> interfaz mediante el uso de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateToolWindow%2A> método.

En este momento, mostrando la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> interfaz proporciona una ventana que contiene una instancia del editor de núcleo.

Sin embargo, esto no es una instancia muy útil, porque no tienen teclas de método abreviado, o tener acceso a características avanzadas. Para obtener acceso a características avanzadas y teclas de método abreviado:

- Use el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> método para asociar un servicio de lenguaje y el objeto de datos que usa el editor.

- Puede crear sus propias claves de acceso directo o utilizar el valor predeterminado del sistema estableciendo el <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> los objetos muestran las propiedades. Para ello, llame a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetGuidProperty%2A> método con el [__VSFPROPID. VSFPROPID_InheritKeyBindings](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_InheritKeyBindings>) propiedad.

   Para obtener y usar las teclas de método abreviado no estándar, generarlos utilizando el *.vsct* archivo. Para obtener más información, consulte [archivos de tabla (.vsct) de comandos de Visual Studio](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

## <a name="how-to-use-an-editor-factory-to-obtain-the-core-editor"></a>Cómo usar un generador de editores para obtener el editor básico

Al implementar un editor básico con un generador del editor mediante el <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> método, siga todos los pasos descritos en la sección anterior para hospedar explícitamente un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> mediante un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> objeto de datos del documento, en un <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> objeto.

Para mostrar el texto, obtener un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaz desde el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> objeto y llamar a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> método.

Para proporcionar un servicio de lenguaje al editor, llame a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> método dentro de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> método.

Para obtener predeterminada teclas de método abreviado, a diferencia de la sección anterior, se usa el contexto de comando devuelto por la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> método al obtener el editor básico de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> método.

Si el <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> método devuelve el mismo comando GUID como el editor de texto, la instancia del editor de núcleo obtiene automáticamente el valor predeterminado teclas de método abreviado.

Para obtener información general, consulte [Tutorial: Creación de un núcleo de editor y registrar un tipo de archivo del editor](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md).

## <a name="see-also"></a>Vea también

- [Dentro del editor de núcleo](../extensibility/inside-the-core-editor.md)
- [Abrir y guardar elementos de proyecto](../extensibility/internals/opening-and-saving-project-items.md)
- [Tutorial: Crear un editor de núcleo y registrar un tipo de archivo del editor](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)