---
title: 'Tutorial: Vinculación de un tipo de contenido a una extensión de nombre de archivo | Documentos de Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e55c06ab5ae07c9b84f9d6462d1a535537e5f69b
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56692845"
---
# <a name="walkthrough-link-a-content-type-to-a-file-name-extension"></a>Tutorial: Vincular un tipo de contenido a una extensión de nombre de archivo
Puede definir su propio tipo de contenido y una extensión de nombre de archivo un vínculo a él mediante el uso de las extensiones de Managed Extensibility Framework (MEF) del editor. En algunos casos, la extensión de nombre de archivo ya está definida por un servicio de lenguaje. Pero, para usarla con MEF, que debe seguir vincularlo a un tipo de contenido.

## <a name="prerequisites"></a>Requisitos previos
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Ha incluido como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Crear un proyecto MEF

1.  Cree un proyecto de VSIX de C#. (En el **nuevo proyecto** cuadro de diálogo, seleccione **Visual C# / extensibilidad**, a continuación, **proyecto VSIX**.) Asigne a la solución el nombre `ContentTypeTest`.

2.  En el **source.extension.vsixmanifest** archivo, vaya a la **activos** pestaña y establezca el **tipo** campo **Microsoft.VisualStudio.MefComponent**, el **origen** campo **un proyecto de la solución actual**y el **proyecto** campo para el nombre del proyecto.

## <a name="define-the-content-type"></a>Definir el tipo de contenido

1.  Agregue un archivo de clase y asígnele el nombre `FileAndContentTypes`.

2.  Agregue referencias a los siguientes ensamblados:

    1.  System.ComponentModel.Composition

    2.  Microsoft.VisualStudio.Text.Logic

    3.  Microsoft.VisualStudio.CoreUtility

3.  Agregue las siguientes `using` directivas.

    ```csharp
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text.Classification;
    using Microsoft.VisualStudio.Utilities;

    ```

4.  Declarar una clase estática que contiene las definiciones.

    ```csharp
    internal static class FileAndContentTypeDefinitions
    {. . .}
    ```

5.  En esta clase, exporte un <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> denominado "hid" y declarar su definición base como "text".

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

-   Para asignar este tipo de contenido a una extensión de nombre de archivo, exportar un <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> que tiene la extensión *.hid* y el tipo de contenido "hid".

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

1.  Crear una extensión del editor. Por ejemplo, puede usar la extensión de glifo de margen que se describe en [Tutorial: Creación de un glifo de margen](../extensibility/walkthrough-creating-a-margin-glyph.md).

2.  Agregue la clase definida en este procedimiento.

3.  Cuando se exporta la clase de extensión, agregue un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de tipo "hid" a él.

    ```csharp
    [Export]
    [ContentType("hid")]
    ```

## <a name="see-also"></a>Vea también
- [Puntos de extensión de editor y el servicio de lenguaje](../extensibility/language-service-and-editor-extension-points.md)