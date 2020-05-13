---
title: 'Tutorial: Vincular un tipo de contenido a una extensión de nombre de archivo . Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 328be013b5d522938cd7450fc53d4866c632abb3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697084"
---
# <a name="walkthrough-link-a-content-type-to-a-file-name-extension"></a>Tutorial: Vincule un tipo de contenido a una extensión de nombre de archivo
Puede definir su propio tipo de contenido y vincular una extensión de nombre de archivo mediante las extensiones de Managed Extensibility Framework (MEF) del editor. En algunos casos, la extensión de nombre de archivo ya está definida por un servicio de lenguaje. Pero, para usarlo con MEF, debe vincularlo a un tipo de contenido.

## <a name="prerequisites"></a>Prerrequisitos
 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en la configuración de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [Instalar el SDK](../extensibility/installing-the-visual-studio-sdk.md)de Visual Studio .

## <a name="create-a-mef-project"></a>Crear un proyecto MEF

1. Cree un proyecto de VSIX de C. (En el cuadro de diálogo **Nuevo proyecto** , seleccione **Visual C/ Extensibilidad**y, a continuación, **Proyecto VSIX**.) Asigne un `ContentTypeTest`nombre a la solución .

2. En el archivo **source.extension.vsixmanifest,** vaya a la pestaña **Assets** y establezca el campo **Type** en **Microsoft.VisualStudio.MefComponent**, el campo **Source** en **A project en la solución actual**y el campo **Project** en el nombre del proyecto.

## <a name="define-the-content-type"></a>Definir el tipo de contenido

1. Agregue un archivo de clase y asígnele el nombre `FileAndContentTypes`.

2. Agregue referencias a los siguientes ensamblados:

    1. System.ComponentModel.Composition

    2. Microsoft.VisualStudio.Text.Logic

    3. Microsoft.VisualStudio.CoreUtility

3. Agregue las `using` siguientes directivas.

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

5. En esta clase, <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> exporte un "hid" con nombre y declare su definición base como "text".

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

- Para asignar este tipo de contenido a <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> una extensión de nombre de archivo, exporte a que tenga la extensión *.hid* y el tipo de contenido "hid".

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

## <a name="add-the-content-type-to-an-editor-export"></a>Agregar el tipo de contenido a una exportación de editor

1. Cree una extensión de editor. Por ejemplo, puede utilizar la extensión de glifo de margen que se describe en [Tutorial: Crear un glifo](../extensibility/walkthrough-creating-a-margin-glyph.md)de margen .

2. Agregue la clase que definió en este procedimiento.

3. Cuando exporte la clase <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de extensión, agregue un tipo "hid" a ella.

    ```csharp
    [Export]
    [ContentType("hid")]
    ```

## <a name="see-also"></a>Vea también
- [Servicio de lenguaje y puntos de extensión del editor](../extensibility/language-service-and-editor-extension-points.md)
