---
title: "TemplateGroupID (Elemento, Plantillas de Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#TemplateGroupID"
helpviewer_keywords: 
  - "<TemplateGroupID> (elemento) [plantillas de Visual Studio]"
  - "TemplateGroupID (elemento) [plantillas de Visual Studio]"
ms.assetid: bce7b49a-90bc-4691-aff3-a87e209f6d83
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# TemplateGroupID (Elemento, Plantillas de Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Especifica en qué tipo de proyecto se mostrará una plantilla de elemento.  Este elemento es significativo cuando [ShowByDefault \(Plantillas de Visual Studio\)](../extensibility/showbydefault-visual-studio-templates.md) está establecido en `false`.  Cuando [ShowByDefault \(Plantillas de Visual Studio\)](../extensibility/showbydefault-visual-studio-templates.md) se establece en `true`, una plantilla de elemento estará disponible en todos los tipos de proyecto.  
  
## Sintaxis  
  
```  
<TemplateGroupID> ... </TemplateGroupID>  
```  
  
## Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### Atributos  
 Ninguno.  
  
### Elementos secundarios  
 Ninguno.  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Clasifica la plantilla y define cómo se muestra en el cuadro de diálogo **Nuevo proyecto** o **Agregar nuevo elemento**.|  
  
## Valor de texto  
 Se requiere un valor de texto.  
  
 El texto especifica un identificador para una categoría de plantillas de elementos.  
  
## Comentarios  
 `TemplateGroupID` es un elemento.  
  
 El valor del elemento `TemplateGroupID` se utiliza junto con el registro del sistema de proyecto \(HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\<version number\>*\\Projects\\\) para filtrar plantillas que aparecen en el cuadro de diálogo **Agregar nuevo elemento**.  
  
|Valor de Visual C\+\+|Significado|  
|---------------------------|-----------------|  
|VC\-Native|Se usa en objetos nativos.  También el valor predeterminado si no se puede determinar un tipo de proyecto.|  
|VC\-Managed|Utilizado para proyectos \(\/ clr\) administrados|  
|VC\-Windows|Utilizado para todos los proyectos destinados a la plataforma de Windows \(nativo\/administrado\/almacén\)|  
|WinRT\-Native\-UAP|Utilizado para proyectos de la Tienda Windows 10|  
|CodeSharing\-Native|Utilizado para proyectos de elementos compartidos|  
|WinRT\-Native\-6.3|Utilizado para proyectos de la Tienda Windows 8.1|  
|WinRT\-Native\-Phone\-6.3|Utilizado para proyectos de Windows Phone 8.1|  
|WinRT\-Native|Utilizado para proyectos de la Tienda Windows 8.0|  
|VC\-Android|Utilizado para proyectos Android|  
  
## Vea también  
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Crear plantillas de proyecto y de elemento personalizadas](../ide/creating-project-and-item-templates.md)