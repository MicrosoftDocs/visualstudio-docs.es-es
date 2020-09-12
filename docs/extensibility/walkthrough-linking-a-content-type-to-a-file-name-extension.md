---
title: Vincular un tipo de contenido a una extensión de nombre de archivo
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3d59ae0b5eb2411ff9e41466e8b87dbe20b835ba
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2020
ms.locfileid: "90034668"
---
# <a name="walkthrough-link-a-content-type-to-a-file-name-extension"></a>Tutorial: vincular un tipo de contenido a una extensión de nombre de archivo
Puede definir su propio tipo de contenido y vincular una extensión de nombre de archivo a él mediante las extensiones del editor Managed Extensibility Framework (MEF). En algunos casos, la extensión de nombre de archivo ya está definida por un servicio de lenguaje. Sin embargo, para usarlo con MEF, debe vincularlo a un tipo de contenido.

## <a name="prerequisites"></a>Requisitos previos
 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS después. Para obtener más información, vea [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Creación de un proyecto MEF

1. Cree un proyecto VSIX en C#. (En el cuadro de diálogo **nuevo proyecto** , seleccione **Visual C#/extensibilidad**y, a continuación, **Proyecto VSIX**). Asigne a la solución el nombre `ContentTypeTest` .

2. En el **archivo source. Extension. vsixmanifest** , vaya a la pestaña **activos** y establezca el campo **tipo** en **Microsoft. VisualStudio. MefComponent**, el campo de **origen** en **un proyecto en la solución actual**y el campo **Project** en el nombre del proyecto.

## <a name="define-the-content-type"></a>Definir el tipo de contenido

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

## <a name="link-a-file-name-extension-to-a-content-type"></a>Vincular una extensión de nombre de archivo a un tipo de contenido

- Para asignar este tipo de contenido a una extensión de nombre de archivo, exporte un <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> que tenga la extensión *. HID* y el tipo de contenido "HID".

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

## <a name="add-the-content-type-to-an-editor-export"></a>Agregar el tipo de contenido a una exportación del editor

1. Cree una extensión de editor. Por ejemplo, puede usar la extensión de glifo de margen que se describe en [Tutorial: crear un glifo de margen](../extensibility/walkthrough-creating-a-margin-glyph.md).

2. Agregue la clase que definió en este procedimiento.

3. Cuando exporte la clase de extensión, agregue una <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de tipo "HID" a ella.

    ```csharp
    [Export]
    [ContentType("hid")]
    ```

## <a name="see-also"></a>Consulte también
- [Puntos de extensión de editor y servicio de lenguaje](../extensibility/language-service-and-editor-extension-points.md)
