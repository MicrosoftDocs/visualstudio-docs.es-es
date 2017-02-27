---
title: "CustomParameters (Elemento, Plantillas de Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameters"
helpviewer_keywords: 
  - "CustomParameters (elemento) [plantillas de proyecto de Visual Studio]"
ms.assetid: cf3efc91-1532-4022-bbb8-a18658424fee
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# CustomParameters (Elemento, Plantillas de Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Agrupa los parámetros personalizados que se pasarán al Asistente de plantilla cuando el asistente realice sustituciones de parámetros.  
  
## Sintaxis  
  
```  
<CustomParameters>  
    <CustomParameter/>  
    <CustomParameter/>  
</CustomParameters>  
```  
  
## Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### Atributos  
 Ninguno.  
  
### Elementos secundarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[CustomParameter](../extensibility/customparameter-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Contiene un nombre de parámetro personalizado y un valor que se usa cuando se crea un proyecto o elemento de la plantilla. Puede haber cero o más elementos `CustomParameter` en un elemento `CustomParameters`.|  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Especifica el contenido de la plantilla.|  
  
## Comentarios  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar varios parámetros personalizados en una plantilla. Cuando se crea un proyecto o elemento de una plantilla con los siguientes parámetros personalizados, todas las instancias de `$color1$` y `$color2$` en la plantilla se reemplazarán los archivos con `Red` y `Blue`, respectivamente.  
  
```  
<CustomParameters>  
    <CustomParameter Name="$color1$" Value="Red"/>  
    <CustomParameter Name="$color2$" Value="Blue "/>  
</CustomParameters>  
```  
  
## Vea también  
 [CustomParameter \(Elemento, Plantillas de Visual Studio\)](../extensibility/customparameter-element-visual-studio-templates.md)   
 [Parámetros de plantilla](../ide/template-parameters.md)   
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)