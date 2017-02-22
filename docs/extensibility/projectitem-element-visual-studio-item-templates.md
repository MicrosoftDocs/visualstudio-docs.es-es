---
title: "ProjectItem (Elemento, Plantillas de elementos de Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem"
helpviewer_keywords: 
  - "<ProjectItem> (elemento) [plantillas de elementos de Visual Studio]"
  - "ProjectItem (elemento) [plantillas de elementos de Visual Studio]"
ms.assetid: 9ed94112-0c38-49df-b728-0dd2d0d1eb47
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# ProjectItem (Elemento, Plantillas de elementos de Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Especifica un archivo que se incluye en la plantilla de elementos.  
  
> [!NOTE]
>  El elemento `ProjectItem` acepta atributos diferentes que dependen de si la plantilla es para un proyecto o un elemento.  En este tema se explica el elemento `ProjectItem` para el elemento.  Para obtener una explicación del elemento `ProjectItem` de las plantillas de proyecto, vea [ProjectItem \(Elemento, Plantillas de proyecto de Visual Studio\)](../extensibility/projectitem-element-visual-studio-project-templates.md).  
  
## Sintaxis  
  
```  
<ProjectItem  
    SubType="Form/Component/CustomControl/UserControl"  
    CustomTool="string"  
    ItemType="string"  
    ReplaceParameters="true/false"  
    TargetFileName="TargetFileName.ext">  
        FileName.ext  
</ProjectItem>  
```  
  
## Atributos y elementos  
 Las siguientes secciones describen atributos, elementos secundarios y elementos primarios.  
  
### Atributos  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`SubType`|Atributo opcional.<br /><br /> Especifica el subtipo de un elemento en una plantilla de elementos de varios archivos.  Este valor se usa para determinar el editor que utilizará [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para abrir el elemento.|  
|`CustomTool`|Atributo opcional.<br /><br /> Establece CustomTool para el elemento en el archivo de proyecto.|  
|`ItemType`|Atributo opcional.<br /><br /> Establece ItemType para el elemento en el archivo de proyecto.|  
|`ReplaceParameters`|Atributo opcional.<br /><br /> Un valor booleano que especifica si el elemento tiene valores de parámetro que se deben reemplazar cuando se crea un proyecto a partir de la plantilla.  El valor predeterminado es `false`.|  
|`TargetFileName`|Atributo opcional.<br /><br /> Especifica el nombre del elemento que se crea a partir de la plantilla.  Este atributo resulta útil para utilizar la sustitución de parámetros para crear un nombre de elemento.|  
  
### Elementos secundarios  
 Ninguno.  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Especifica el contenido de la plantilla.|  
  
## Valor de texto  
 Se requiere un valor de texto.  
  
 `string` que representa el nombre de un archivo del archivo .zip de plantillas.  
  
## Comentarios  
 `ProjectItem` es un elemento opcional de `TemplateContent`.  
  
 El atributo `TargetFileName` se puede utilizar para cambiar el nombre de los archivos con parámetros.  Por ejemplo, si existe el archivo `MyFile.vb` en el directorio raíz del archivo .zip de plantillas, pero desea que se le asigne al archivo un nombre basado en el nombre de archivo facilitado por el usuario en el cuadro de diálogo **Agregar nuevo elemento**, utilizaría el siguiente código XML:  
  
```  
<ProjectItem TargetFileName="$fileinputname$.vb">MyFile.vb</ProjectItem>  
```  
  
 Cuando se crea un elemento a partir de esta plantilla, el nombre de archivo se basará en el nombre del usuario especificado en el cuadro de diálogo **Agregar nuevo elemento**.  Esto es útil al crear plantillas de elementos de varios archivos.  Para obtener más información, vea [Cómo: Crear plantillas de elementos de varios archivos](../ide/how-to-create-multi-file-item-templates.md) y [Parámetros de plantilla](../ide/template-parameters.md).  
  
## Ejemplo  
 En el ejemplo siguiente se muestran los metadatos de una plantilla de elementos estándar de una clase de [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <DefaultName>MyClass.cs</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem ReplaceParameters="true">MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## Vea también  
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Crear plantillas de proyecto y de elemento personalizadas](../ide/creating-project-and-item-templates.md)   
 [Cómo: Crear plantillas de elementos de varios archivos](../ide/how-to-create-multi-file-item-templates.md)   
 [Parámetros de plantilla](../ide/template-parameters.md)