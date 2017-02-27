---
title: "DefaultName (Elemento, Plantillas de Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#DefaultName"
helpviewer_keywords: 
  - "DefaultName (elemento) [plantillas de proyecto de Visual Studio]"
ms.assetid: 0ff056c8-b9d2-4747-9308-92adf1811491
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# DefaultName (Elemento, Plantillas de Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Especifica el nombre que generará el sistema de proyectos de Visual Studio para el proyecto o elemento cuando se cree.  
  
## Sintaxis  
  
```  
<DefaultName>  
    Default Project Name  
</DefaultName>  
```  
  
## Atributos y elementos  
 En las próximas secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### Atributos  
 Ninguno.  
  
### Elementos secundarios  
 Ninguno.  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Categoriza la plantilla y define cómo se muestra en el cuadro de diálogo **Nuevo proyecto** o **Agregar nuevo elemento**.|  
  
## Valor de texto  
 Se requiere un valor de texto.  
  
 Este texto especifica el nombre predeterminado del proyecto o elemento.  
  
## Comentarios  
 `DefaultName` es un elemento opcional.  
  
 Para los proyectos, este elemento especifica el nombre del directorio donde se almacena el proyecto en el disco.  Para los elementos, especifica el nombre de archivo del archivo de código fuente.  
  
 Cuando se crea un proyecto o un elemento, puede modificar el nombre predeterminado mediante la opción **Nombre** , que está disponible en el cuadro de diálogo **Nuevo proyecto** o el cuadro de diálogo **Agregar nuevo elemento** .  
  
 Si no desea que el sistema de proyecto genere el nombre predeterminado del proyecto o elemento, establezca el elemento [ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md) en `False`.  
  
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