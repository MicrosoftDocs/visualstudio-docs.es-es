---
title: Procedimiento Creación de plantillas de elementos de varios archivos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, creating multi-file item templates
- multi-file item templates
- item templates, creating multi-file item templates
ms.assetid: fe3c4257-e383-4c80-b8af-c5c521959c33
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4616cb2f0e908b3228061288da05ce01543afdc4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54785905"
---
# <a name="how-to-create-multi-file-item-templates"></a>Cómo: Crear plantillas de elementos de varios archivos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede que las plantillas de elementos solo especifiquen un elemento, pero a veces el elemento se compone de varios archivos. Por ejemplo, una plantilla de elemento de Windows Forms para Visual Basic requiere los tres archivos siguientes:  
  
- Un archivo .vb que contiene el código del formulario.  
  
- Un archivo .designer.vb que contiene la información del diseñador para el formulario.  
  
- Un archivo .resx que contiene los recursos incrustados del formulario.  
  
  Las plantillas de elementos de varios archivos requieren parámetros para garantizar que se usan las extensiones de nombre de archivo correctas cuando se crea el elemento en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Si crea una plantilla de elemento mediante el **Asistente para exportar plantillas**, estos parámetros se generan automáticamente y no se requiere ninguna otra edición. En los pasos siguientes, se explica cómo usar parámetros para garantizar que se crean las extensiones de nombre de archivo correctas.  
  
### <a name="to-manually-create-a-multi-file-item-template"></a>Para crear manualmente una plantilla de elemento de varios archivos  
  
1.  Cree la plantilla de elemento tal y como crearía una plantilla de elemento de un único archivo. Para más información, vea [Cómo: Crear plantillas de elementos](../ide/how-to-create-item-templates.md).  
  
2.  Agregue atributos `TargetFileName` a cada elemento `ProjectItem`. Establezca los valores de los atributos `TargetFileName` en $fileinputname$.*extensiónArchivo*, donde *extensiónArchivo* es la extensión de nombre de archivo del archivo que se incluye en la plantilla. Por ejemplo:  
  
    ```  
    <ProjectItem TargetFileName="$fileinputname$.vb">  
        Form1.vb  
    </ProjectItem>  
    <ProjectItem TargetFileName="$fileinputname$.Designer.vb">  
        Form1.Designer.vb  
    </ProjectItem>  
    <ProjectItem TargetFileName="$fileinputname$.resx">  
        Form1.resx  
    </ProjectItem>  
    ```  
  
     Cuando se agrega un elemento derivado de esta plantilla a un proyecto, los nombres de archivo se basarán en el nombre que ha escrito el usuario en el cuadro de diálogo **Agregar nuevo elemento**.  
  
3.  Seleccione los archivos que se incluirán en la plantilla, haga clic con el botón derecho en la selección, elija **Enviar a** y, después, **Carpeta comprimida (en zip)**. Los archivos seleccionados se comprimen en un archivo .zip.  
  
4.  Coloque el archivo .zip en la ubicación de la plantilla de elemento del usuario. De forma predeterminada, el directorio es \Mis documentos\Visual Studio *Versión*\Templates\ItemTemplates\\. Para más información, vea [Cómo: Localizar y organizar plantillas](../ide/how-to-locate-and-organize-project-and-item-templates.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente, se muestra una plantilla de Windows Forms de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Cuando se crea un elemento basado en esta plantilla, los nombres de los tres archivos creados coincidirán con el nombre especificado en el cuadro de diálogo **Agregar nuevo elemento**.  
  
```  
<VSTemplate Version="2.0.0" Type="Item"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>Multi-file Item Template</Name>  
        <Icon>Icon.ico</Icon>  
        <Description>An example of a multi-file item template</Description>  
        <ProjectType>VisualBasic</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem TargetFileName="$fileinputname$.vb" SubType="Form">  
            Form1.vb  
        </ProjectItem>  
        <ProjectItem TargetFileName="$fileinputname$.Designer.vb">  
            Form1.Designer.vb  
        </ProjectItem>  
        <ProjectItem TargetFileName="$fileinputname$.resx">  
            Form1.resx  
        </ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Vea también  
 [Crear plantillas para proyectos y elementos en Visual Studio](../ide/creating-project-and-item-templates.md)   
 [Cómo: Crear plantillas de elementos](../ide/how-to-create-item-templates.md)   
 [Parámetros de plantilla](../ide/template-parameters.md)   
 [Cómo: Sustituir parámetros en una plantilla](../ide/how-to-substitute-parameters-in-a-template.md)
