---
title: "MaxFrameworkVersion (Elemento, Plantillas de Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "<MaxFrameworkVersion> (Elemento, Plantillas de Visual Studio)"
  - "MaxFrameworkVersion (Elemento, Plantillas de Visual Studio)"
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# MaxFrameworkVersion (Elemento, Plantillas de Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Especifica la versión máxima de .NET Framework requerida por la plantilla.  Determina si la plantilla se muestra en la sección **Plantillas** del cuadro de diálogo **Agregar nuevo proyecto** en función del valor seleccionado en el cuadro **Versión de .NET Framework de destino** del cuadro de diálogo **Agregar nuevo proyecto**.  
  
## Sintaxis  
  
```  
<MaxFrameworkVersion> ... </MaxFrameworkVersion>  
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
  
 El texto debe ser el número de versión de .NET Framework más reciente permitido por la plantilla.  
  
## Comentarios  
 `MaxFrameworkVersion` es un elemento opcional.  El elemento de la sección `TemplateData` del archivo .vstemplate actúa como filtro de la sección de **Plantillas** del cuadro de diálogo **Agregar nuevo proyecto**.  Solamente se mostrarán las plantillas cuyos requisitos de .NET Framework sean inferiores a los valores del elemento `MaxFrameworkVersion`, basándose en el valor seleccionado en el recuadro **Versión de .NET Framework de destino** del cuadro de diálogo **Agregar nuevo proyecto**.  El elemento `MaxFrameworkVersion` debe omitirse a menos que sea necesario, para no impedir por error que se muestren la plantillas al usarlas con las versiones más recientes de .NET Framework.  
  
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
        <MaxFrameworkVersion>3.5</MaxFrameworkVersion>  
        <DefaultName>MyClass</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 En este ejemplo, la versión máxima de .NET Framework requerida por la plantilla, representada por `MaxFrameworkVersion`, es la 3.5.  La plantilla anterior solo se mostrará al seleccionar 3.0 ó 3.5 en el cuadro **Versión de .NET Framework de destino** del cuadro de diálogo **Agregar nuevo proyecto**.  
  
## Vea también  
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Crear plantillas de proyecto y de elemento personalizadas](../ide/creating-project-and-item-templates.md)