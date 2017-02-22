---
title: "ProvideDefaultName (Elemento, Plantillas de Visual Studio) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/vstemplate/2005#ProvideDefaultName"
helpviewer_keywords: 
  - "ProvideDefaultName (elemento) [plantillas de proyecto de Visual Studio]"
ms.assetid: 7b0e7b20-fd6b-42e2-81d0-e5100cea0528
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# ProvideDefaultName (Elemento, Plantillas de Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Especifica si el sistema de proyecto de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] generará un nombre predeterminado para la plantilla en el cuadro de diálogo **Agregar nuevo elemento** o **Nuevo proyecto**.  
  
## Sintaxis  
  
```  
<ProvideDefaultName> true/false </ProvideDefaultName>  
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
  
 El texto debe ser `true` o `false`, que indica si se deberá generar o no un nombre predeterminado para la plantilla en el cuadro de diálogo **Agregar nuevo elemento** o **Nuevo proyecto**.  
  
## Comentarios  
 `ProvideDefaultName` es un elemento opcional.  El valor predeterminado es `true`.  
  
 Si el elemento `ProvideDefaultName` es `false`, los cuadros **Nombre** de los cuadros de diálogo **Agregar nuevo elemento** y **Nuevo proyecto** contendrán el valor `<Insertar nombre>`.  
  
 Utilice el elemento [DefaultName](../extensibility/defaultname-element-visual-studio-templates.md) para especificar el nombre predeterminado del proyecto o elemento en los cuadros de diálogo **Agregar nuevo elemento** y **Nuevo proyecto**.  
  
## Ejemplo  
 En el ejemplo de código siguiente se establece el elemento `ProvideDefaultName` en `false`.  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <ProvideDefaultName>false</ProvideDefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## Vea también  
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Crear plantillas de proyecto y de elemento personalizadas](../ide/creating-project-and-item-templates.md)