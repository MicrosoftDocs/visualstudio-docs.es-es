---
title: "CustomParameter (Elemento, Plantillas de Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameter"
helpviewer_keywords: 
  - "CustomParameters (elemento) [plantillas de proyecto de Visual Studio]"
ms.assetid: 743c4489-74ac-403a-bbaa-eed7d785a3ac
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# CustomParameter (Elemento, Plantillas de Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Contiene un nombre y un valor de parámetro personalizados que se usarán cuando se cree un proyecto o elemento a partir de la plantilla.  
  
## Sintaxis  
  
```  
<CustomParameter Name="name" Value="value">  
```  
  
## Atributos y elementos  
 En las próximas secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### Atributos  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`Name`|Requerido.  Nombre del parámetro.  El formato del parámetro es $*nombre*$.|  
|`Value`|Requerido.  Valor de reemplazo del parámetro.|  
  
### Elementos secundarios  
 Ninguno.  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Agrupa los parámetros personalizados que se van a pasar al asistente de la plantilla cuando el asistente realice sustituciones de parámetros.|  
  
## Comentarios  
 Cuando una plantilla contiene elementos `CustomParameter`, cada instancia del atributo `Name` se reemplaza con el atributo `Value` en los archivos del proyecto o elemento que se ha creado.  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo utilizar varios parámetros personalizados en una plantilla.  Cuando se cree un proyecto o elemento a partir de una plantilla mediante los siguientes parámetros personalizados, todas las instancias de `$color1$` y `$color2$` en los archivos de plantilla se sustituirán por `Red` y `Blue`, respectivamente.  
  
```  
<CustomParameters>  
    <CustomParameter Name="$color1$" Value="Red"/>  
    <CustomParameter Name="$color2$" Value="Blue "/>  
</CustomParameters>  
```  
  
## Vea también  
 [CustomParameters \(Elemento, Plantillas de Visual Studio\)](../extensibility/customparameters-element-visual-studio-templates.md)   
 [Parámetros de plantilla](../ide/template-parameters.md)   
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)