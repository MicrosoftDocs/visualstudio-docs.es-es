---
title: "SortOrder (Elemento, Plantillas de Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#SortOrder"
helpviewer_keywords: 
  - "<SortOrder> (elemento) [plantillas de Visual Studio]"
  - "SortOrder (elemento) [plantillas de Visual Studio]"
ms.assetid: 151932c1-f08a-4f78-a8d0-bd2f32211a9c
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# SortOrder (Elemento, Plantillas de Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Especifica un valor que se utiliza para organizar la plantilla, entre otras plantillas de la misma categoría, tal como aparece en el cuadro de diálogo **Nuevo proyecto** o **Agregar nuevo elemento**.  
  
## Sintaxis  
  
```  
<SortOrder> ... </SortOrder>  
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
  
 `integer` que representa el valor del criterio de ordenación.  
  
## Comentarios  
 `SortOrder` es un elemento opcional.  El valor predeterminado es 100 y todos los valores deben ser múltiplos de 10.  
  
 El elemento `SortOrder` se omite para las plantillas creadas por el usuario.  Todas las plantillas creadas por el usuario se ordenan alfabéticamente.  
  
 Las plantillas con criterios de ordenación con valores bajos aparecen en el cuadro de diálogo **Nuevo proyecto** o **Agregar nuevo elemento** antes que las que tienen criterios de ordenación con valores altos.  
  
## Ejemplo  
 En el ejemplo siguiente se muestran los metadatos de una plantilla de clase estándar de [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class template.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <SortOrder>290</SortOrder>  
        <DefaultName>MyClass</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 En este ejemplo, el elemento `SortOrder` es relativamente alto.  Es probable que las demás plantillas de elementos de [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] tengan un valor de `SortOrder` menor que `290` y que aparezcan antes de esta en el cuadro de diálogo **Nuevo elemento**.  
  
## Vea también  
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Crear plantillas de proyecto y de elemento personalizadas](../ide/creating-project-and-item-templates.md)