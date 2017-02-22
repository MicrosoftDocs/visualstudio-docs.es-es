---
title: "Assembly (Elemento, Plantillas de Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#Assembly"
helpviewer_keywords: 
  - "Assembly (elemento) [plantillas de Visual Studio]"
  - "elemento <Assembly> [plantillas de Visual Studio]"
ms.assetid: 9242f76a-1273-4b8a-8f26-6606f91829ef
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Assembly (Elemento, Plantillas de Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Especifica información sobre un ensamblado, que la plantilla utiliza para agregar una referencia de ese ensamblado a los proyectos.  
  
## Sintaxis  
  
```  
<Assembly> AssemblyName </Assembly>  
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
|[Referencia](../extensibility/reference-element-visual-studio-templates.md)|Especifica la referencia de ensamblado que se debe agregar cuando el elemento se agrega a un proyecto.|  
  
## Valor de texto  
 Se requiere un valor de texto.  
  
 Este texto especifica el ensamblado que se debe agregar a un proyecto cuando se crea una instancia de la plantilla de elementos.  El nombre de este ensamblado se debe especificar en una de las siguientes maneras:  
  
-   Como un nombre de ensamblado completo.  Por ejemplo:  
  
    ```  
    <Assembly>  
        MyAssembly, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom = null.  
    </Assembly>  
    ```  
  
-   Como referencia de texto simple.  Por ejemplo:  
  
    ```  
    <Assembly> System </Assembly>  
    ```  
  
## Comentarios  
 `Assembly` es un elemento secundario necesario de `Reference`.  
  
 Los elementos `Reference`, `References,` y `Assembly` sólo se pueden utilizar en archivos .vstemplate que tienen un valor de atributo `Type` de `Item`.  
  
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