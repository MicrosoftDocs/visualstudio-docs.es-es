---
title: SortOrder (elemento) (plantillas de Visual Studio) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SortOrder
helpviewer_keywords:
- SortOrder element [Visual Studio Templates]
- <SortOrder> element [Visual Studio Templates]
ms.assetid: 151932c1-f08a-4f78-a8d0-bd2f32211a9c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b963b6e74b7c24d31ddc611407df22380ff8bb60
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31140328"
---
# <a name="sortorder-element-visual-studio-templates"></a>SortOrder (Elemento, Plantillas de Visual Studio)
Especifica un valor que se utiliza para organizar la plantilla, entre otras plantillas de la misma categoría, tal y como aparece en la vista la **nuevo proyecto** o **Agregar nuevo elemento** cuadro de diálogo.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<SortOrder >  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<SortOrder> ... </SortOrder>  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
 Ninguno.  
  
### <a name="child-elements"></a>Elementos secundarios  
 Ninguno.  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Clasifica la plantilla y define cómo se muestra en el cuadro de diálogo **Nuevo proyecto** o **Agregar nuevo elemento** .|  
  
## <a name="text-value"></a>Valor de texto  
 Se requiere un valor de texto.  
  
 Un `integer` que representa el valor de criterio de ordenación.  
  
## <a name="remarks"></a>Comentarios  
 `SortOrder` es un elemento opcional. El valor predeterminado es 100 y todos los valores deben ser múltiplos de 10.  
  
 El `SortOrder` elemento se omite para plantillas creadas por el usuario. Todas las plantillas creadas por el usuario se ordenan alfabéticamente.  
  
 Plantillas que tienen valores de ordenación bajos aparecen en la vista la **nuevo proyecto** o **Agregar nuevo elemento** cuadro de diálogo antes de plantillas que tienen valores de ordenación altos.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra los metadatos de un estándar [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] plantilla de clase.  
  
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
  
 En este ejemplo, el `SortOrder` elemento es relativamente alto. Es probable que otros [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] plantillas de elementos tendrá un `SortOrder` valor inferior al `290` y que aparezcan antes de esta plantilla en el **nuevo elemento** cuadro de diálogo.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Crear plantillas para proyectos y elementos en Visual Studio](../ide/creating-project-and-item-templates.md)