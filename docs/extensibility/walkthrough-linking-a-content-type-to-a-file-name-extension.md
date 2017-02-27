---
title: "Tutorial: Vincular un tipo de contenido a una extensi&#243;n de nombre de archivo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editores [Visual Studio SDK], vinculan nuevo: tipo de contenido a la extensión de nombre de archivo"
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
caps.latest.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 24
---
# Tutorial: Vincular un tipo de contenido a una extensi&#243;n de nombre de archivo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede definir su propio tipo de contenido y vincular una extensión de nombre de archivo mediante el uso de extensiones de editor de Managed Extensibility Framework \(MEF\). En algunos casos, la extensión de nombre de archivo ya está definida por un servicio de lenguaje; No obstante, para utilizar con MEF que todavía debe vincularlo a un tipo de contenido.  
  
## Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional de la instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulta [Instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Crear un proyecto MEF  
  
1.  Cree un proyecto de VSIX de C\#. \(En el **nuevo proyecto** cuadro de diálogo, seleccione **Visual C\# \/ extensibilidad**, a continuación, **proyecto VSIX**.\) El nombre de la solución `ContentTypeTest`.  
  
2.  En el **source.extension.vsixmanifest** archivo, vaya a la **activos** pestaña y establecer el **tipo** campo **Microsoft.VisualStudio.MefComponent**, el **origen** campo **un proyecto de la solución actual**, y el **proyecto** en el nombre del proyecto.  
  
## Definir el tipo de contenido  
  
1.  Agregue un archivo de clase y asígnele el nombre `FileAndContentTypes`.  
  
2.  Agregue referencias a los siguientes ensamblados:  
  
    1.  System.ComponentModel.Composition  
  
    2.  Microsoft.VisualStudio.Text.Logic  
  
    3.  Microsoft.VisualStudio.CoreUtility  
  
3.  Agregue las siguientes `using` directivas.  
  
    ```c#  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text.Classification;  
    using Microsoft.VisualStudio.Utilities;  
  
    ```  
  
4.  Declare una clase estática que contiene las definiciones.  
  
    ```c#  
    internal static class FileAndContentTypeDefinitions  
    {. . .}  
    ```  
  
5.  En esta clase, exportar un <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> denominado "hid" y declarar su definición base como "text".  
  
    ```c#  
    internal static class FileAndContentTypeDefinitions  
    {  
        [Export]  
        [Name("hid")]  
        [BaseDefinition("text")]  
        internal static ContentTypeDefinition hidingContentTypeDefinition;  
    }  
    ```  
  
## Vinculación de una extensión de nombre de archivo a un tipo de contenido  
  
-   Para asignar este tipo de contenido a una extensión de nombre de archivo, exporte una <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> que tiene la extensión ".hid" y el tipo de contenido "hid".  
  
    ```c#  
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
  
## Agregar el tipo de contenido a una exportación de Editor  
  
1.  Crear una extensión del editor. Por ejemplo, puede usar la extensión de glifo de margen se describe en [Tutorial: Crear un glifo de margen](../extensibility/walkthrough-creating-a-margin-glyph.md).  
  
2.  Agregue la clase definida en este procedimiento.  
  
3.  Cuando se exporta la clase de extensión, agregue un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> del tipo "hid" a él.  
  
    ```c#  
    [Export]  
    [ContentType("hid")]  
    ```  
  
## Vea también  
 [Servicio de lenguaje y los puntos de extensión del Editor](../extensibility/language-service-and-editor-extension-points.md)