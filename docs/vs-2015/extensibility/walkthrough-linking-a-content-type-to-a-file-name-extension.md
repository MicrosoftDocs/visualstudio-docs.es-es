---
title: 'Tutorial: Vinculación de un tipo de contenido a una extensión de nombre de archivo | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
caps.latest.revision: 25
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1742da19e2d99cbb22d930b7146b1f9859e19cef
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47583006"
---
# <a name="walkthrough-linking-a-content-type-to-a-file-name-extension"></a>Tutorial: Vinculación de un tipo de contenido con una extensión de nombre de archivo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Tutorial: vinculación de un tipo de contenido a una extensión de nombre de archivo](https://docs.microsoft.com/visualstudio/extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension).  
  
Puede definir su propio tipo de contenido y una extensión de nombre de archivo un vínculo a él mediante el uso de extensiones de editor de Managed Extensibility Framework (MEF). En algunos casos, la extensión de nombre de archivo ya está definida por un servicio de lenguaje; No obstante, para usarlo con MEF que todavía debe vincularlo a un tipo de contenido.  
  
## <a name="prerequisites"></a>Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Creación de un proyecto MEF  
  
1.  Cree un proyecto de VSIX de C#. (En el **nuevo proyecto** cuadro de diálogo, seleccione **Visual C# / extensibilidad**, a continuación, **proyecto VSIX**.) Nombre de la solución `ContentTypeTest`.  
  
2.  En el **source.extension.vsixmanifest** archivo, vaya a la **activos** pestaña y establezca el **tipo** campo **Microsoft.VisualStudio.MefComponent**, el **origen** campo **un proyecto de la solución actual**y el **proyecto** campo para el nombre del proyecto.  
  
## <a name="defining-the-content-type"></a>Definir el tipo de contenido  
  
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
  
## <a name="linking-a-file-name-extension-to-a-content-type"></a>Vinculación de una extensión de nombre de archivo a un tipo de contenido  
  
-   Para asignar este tipo de contenido a una extensión de nombre de archivo, exportar un <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> que tiene la extensión ".hid" y el tipo de contenido "hid".  
  
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
  
## <a name="adding-the-content-type-to-an-editor-export"></a>Agregar el tipo de contenido a una exportación de Editor  
  
1.  Crear una extensión del editor. Por ejemplo, puede usar la extensión de glifo de margen que se describe en [Tutorial: creación de un glifo de margen](../extensibility/walkthrough-creating-a-margin-glyph.md).  
  
2.  Agregue la clase definida en este procedimiento.  
  
3.  Cuando se exporta la clase de extensión, agregue un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de tipo "hid" a él.  
  
    ```csharp  
    [Export]  
    [ContentType("hid")]  
    ```  
  
## <a name="see-also"></a>Vea también  
 [Servicio de lenguaje y puntos de extensión del editor](../extensibility/language-service-and-editor-extension-points.md)

