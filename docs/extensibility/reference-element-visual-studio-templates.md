---
title: "Reference (Elemento, Plantillas de Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#Reference"
helpviewer_keywords: 
  - "<Reference> (elemento) [plantillas de Visual Studio]"
  - "Reference (elemento) [plantillas de Visual Studio]"
ms.assetid: 852772ea-c324-42e9-8c8a-6d565414a109
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Reference (Elemento, Plantillas de Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Especifica la referencia de ensamblado que se debe agregar cuando el elemento se agrega a un proyecto.  
  
## Sintaxis  
  
```  
<Reference>  
    <Assembly> ... </Assembly>  
</Reference>  
```  
  
## Atributos y elementos  
 Las siguientes secciones describen atributos, elementos secundarios y elementos primarios.  
  
### Atributos  
 Ninguno.  
  
### Elementos secundarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[Ensamblado](../extensibility/assembly-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Especifica información sobre un ensamblado, que la plantilla utiliza para agregar una referencia de ese ensamblado a los proyectos.  Debe haber exactamente un elemento `Assembly` en cada elemento `Reference`.|  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[Referencias](../extensibility/references-element-visual-studio-templates.md)|Agrupa las referencias de ensamblado que la plantilla agrega a los proyectos.|  
  
## Comentarios  
 `Reference` es un elemento secundario necesario de `References`.  
  
 Los elementos `Reference` y `References` sólo se pueden utilizar en archivos .vstemplate cuyo valor del atributo `Type` sea `Item`.  
  
## Ejemplo  
 El ejemplo siguiente muestra el elemento `TemplateContent` de una plantilla de elementos.  Este código XML agrega referencias a los ensamblados System.dll y System.Data.dll.  
  
```  
<TemplateContent>  
    <References>  
        <Reference>  
            <Assembly>  
                System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
        <Reference>  
            <Assembly>  
                System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
    </References>  
    ...  
</TemplateContent>  
```  
  
## Vea también  
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Crear plantillas de proyecto y de elemento personalizadas](../ide/creating-project-and-item-templates.md)