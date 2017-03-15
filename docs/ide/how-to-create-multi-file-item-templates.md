---
title: "C&#243;mo: Crear plantillas de elementos de varios archivos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "plantillas de elementos, crear plantillas de elementos de varios archivos"
  - "plantillas de elementos de varios archivos"
  - "plantillas de Visual Studio, crear plantillas de elementos de varios archivos"
ms.assetid: fe3c4257-e383-4c80-b8af-c5c521959c33
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# C&#243;mo: Crear plantillas de elementos de varios archivos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Las plantillas de elementos sólo pueden especificar uno elemento, pero a veces el elemento se compone de varios archivos.  Por ejemplo, una plantilla de elemento de formularios Windows Forms para Visual Basic requiere los tres archivos siguientes:  
  
-   Un archivo .vb que contiene el código del formulario.  
  
-   Un archivo .vb que contiene la información del diseñador del formulario.  
  
-   Un archivo .resx que contiene los recursos incrustados del formulario.  
  
 Las plantillas de elementos de varios archivos requieren el uso de parámetros para garantizar que se usan las extensiones de nombre de archivo correctas cuando se crea el elemento en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Si crea una plantilla de elementos mediante el **Asistente para exportar plantillas**, se generarán estos parámetros automáticamente y no hará falta ninguna edición adicional.  En los pasos siguientes se explica cómo usar los parámetros para garantizar que se crean las extensiones de nombre de archivo correctas.  
  
### Para crear manualmente una plantilla de elementos de varios archivos  
  
1.  Cree la plantilla de elementos de la misma manera que lo haría con una plantilla de elementos de un único archivo.  Para obtener más información, vea [Cómo: Crear plantillas de elementos](../ide/how-to-create-item-templates.md).  
  
2.  Agregue atributos `TargetFileName` a cada elemento `ProjectItem`.  Establezca los valores de los atributos `TargetFileName` en $fileinputname$.*extensiónDeArchivo*, donde *extensiónDeArchivo* es la extensión de nombre de archivo del archivo que se incluye en la plantilla.  Por ejemplo:  
  
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
  
     Cuando se agrega a un proyecto un elemento procedente de esta plantilla, los nombres de archivo se basan en el nombre que el usuario escribió en el cuadro de diálogo **Agregar nuevo elemento**.  
  
3.  Seleccione los archivos que se van a incluir en la plantilla, haga clic con el botón secundario del mouse en la selección, haga clic en **Enviar a** y, a continuación, haga clic en **Carpeta comprimida \(en zip\)**.  Los archivos seleccionados se comprimen en un archivo .zip.  
  
4.  Coloque el archivo .zip en la ubicación de la plantilla de elementos de usuario.  de forma predeterminada, el directorio es \\My Documents\\Visual Studio *Versión*\\Templates\\ItemTemplates \\.  Para obtener más información, vea [Cómo: Localizar y organizar plantillas](../ide/how-to-locate-and-organize-project-and-item-templates.md).  
  
## Ejemplo  
 En el ejemplo siguiente se muestra una plantilla de Windows Forms de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Cuando se crea un elemento basado en esta plantilla, los nombres de los tres archivos creados coincidirán con el nombre especificado en el cuadro de diálogo **Agregar nuevo elemento**.  
  
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
  
## Vea también  
 [Crear plantillas de proyecto y de elemento personalizadas](../ide/creating-project-and-item-templates.md)   
 [Cómo: Crear plantillas de elementos](../ide/how-to-create-item-templates.md)   
 [Parámetros de plantilla](../ide/template-parameters.md)   
 [Cómo: Sustituir parámetros en una plantilla](../ide/how-to-substitute-parameters-in-a-template.md)