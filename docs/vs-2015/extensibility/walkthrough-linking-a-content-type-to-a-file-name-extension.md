---
title: 'Tutorial: vincular un tipo de contenido a una extensión de nombre de archivo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: beae9d0526cb9f2f294f2267a8da52d3ce3d8c08
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201996"
---
# <a name="walkthrough-linking-a-content-type-to-a-file-name-extension"></a>Tutorial: Vinculación de un tipo de contenido con una extensión de nombre de archivo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede definir su propio tipo de contenido y vincular una extensión de nombre de archivo a él mediante las extensiones del editor Managed Extensibility Framework (MEF). En algunos casos, la extensión de nombre de archivo ya se ha definido mediante un servicio de lenguaje; No obstante, para usarlo con MEF, todavía debe vincularlo a un tipo de contenido.  
  
## <a name="prerequisites"></a>Prerrequisitos  
 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Crear un proyecto MEF  
  
1. Cree un proyecto VSIX en C#. (En el cuadro de diálogo **nuevo proyecto** , seleccione **Visual C#/extensibilidad**y, a continuación, **Proyecto VSIX**). Asigne a la solución el nombre `ContentTypeTest` .  
  
2. En el **archivo source. Extension. vsixmanifest** , vaya a la pestaña **activos** y establezca el campo **tipo** en **Microsoft. VisualStudio. MefComponent**, el campo de **origen** en **un proyecto en la solución actual**y el campo **Project** en el nombre del proyecto.  
  
## <a name="defining-the-content-type"></a>Definir el tipo de contenido  
  
1. Agregue un archivo de clase y asígnele el nombre `FileAndContentTypes`.  
  
2. Agregue referencias a los siguientes ensamblados:  
  
    1. System.ComponentModel.Composition  
  
    2. Microsoft. VisualStudio. Text. Logic  
  
    3. Microsoft. VisualStudio. CoreUtility  
  
3. Agregue las siguientes `using` directivas.  
  
    ```csharp  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text.Classification;  
    using Microsoft.VisualStudio.Utilities;  
  
    ```  
  
4. Declare una clase estática que contenga las definiciones.  
  
    ```csharp  
    internal static class FileAndContentTypeDefinitions  
    {. . .}  
    ```  
  
5. En esta clase, exporte un <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> "HID" con nombre y declare su definición base como "Text".  
  
    ```csharp  
    internal static class FileAndContentTypeDefinitions  
    {  
        [Export]  
        [Name("hid")]  
        [BaseDefinition("text")]  
        internal static ContentTypeDefinition hidingContentTypeDefinition;  
    }  
    ```  
  
## <a name="linking-a-file-name-extension-to-a-content-type"></a>Vincular una extensión de nombre de archivo a un tipo de contenido  
  
- Para asignar este tipo de contenido a una extensión de nombre de archivo, exporte un <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> que tenga la extensión ". HID" y el tipo de contenido "HID".  
  
    ```csharp  
    internal static class FileAndContentTypeDefinitions  
    {  
         [Export]  
         [Name("hid")]  
         [BaseDefinition("text")]  
        internal static ContentTypeDefinition hidingContentTypeDefinition;  
  
         [Export]  
         [FileExtension(".hid")]  
         [ContentType("hid")]  
        internal static FileExtensionToContentTypeDefinition hiddenFileExtensionDefinition;  
    }  
    ```  
  
## <a name="adding-the-content-type-to-an-editor-export"></a>Agregar el tipo de contenido a una exportación del editor  
  
1. Cree una extensión de editor. Por ejemplo, puede usar la extensión de glifo de margen que se describe en [Tutorial: crear un glifo de margen](../extensibility/walkthrough-creating-a-margin-glyph.md).  
  
2. Agregue la clase que definió en este procedimiento.  
  
3. Cuando exporte la clase de extensión, agregue una <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de tipo "HID" a ella.  
  
    ```csharp  
    [Export]  
    [ContentType("hid")]  
    ```  
  
## <a name="see-also"></a>Consulte también  
 [Servicio de lenguaje y puntos de extensión del editor](../extensibility/language-service-and-editor-extension-points.md)
