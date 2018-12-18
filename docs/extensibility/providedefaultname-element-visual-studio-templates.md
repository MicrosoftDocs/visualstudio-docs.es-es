---
title: ProvideDefaultName (elemento) (plantillas de Visual Studio) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProvideDefaultName
helpviewer_keywords:
- ProvideDefaultName element [Visual Studio project templates]
ms.assetid: 7b0e7b20-fd6b-42e2-81d0-e5100cea0528
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a187df0e50a2948ab6f1ef3a0fffea651dca23b9
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39636017"
---
# <a name="providedefaultname-element-visual-studio-templates"></a>ProvideDefaultName (elemento) (plantillas de Visual Studio)
Especifica si el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sistema del proyecto generará un nombre predeterminado para la plantilla en el **Agregar nuevo elemento** o **nuevo proyecto** cuadro de diálogo.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<ProvideDefaultName >  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
<ProvideDefaultName> true/false </ProvideDefaultName>  
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
  
 El texto debe ser `true` o `false`, que indica si se debe o no generar un nombre predeterminado para la plantilla en el **Agregar nuevo elemento** o **nuevo proyecto** cuadro de diálogo.  
  
## <a name="remarks"></a>Comentarios  
 `ProvideDefaultName` es un elemento opcional. El valor predeterminado es `true`.  
  
 Si el `ProvideDefaultName` es elemento `false`, el **nombre** cuadros de la **Agregar nuevo elemento** y **nuevo proyecto** cuadros de diálogo contienen el valor `<Enter_name>`.  
  
 Use la [DefaultName](../extensibility/defaultname-element-visual-studio-templates.md) elemento para especificar el nombre predeterminado del proyecto o elemento en el **Agregar nuevo elemento** y **nuevo proyecto** cuadros de diálogo. Cuando el valor de la `ProvideDefaultName` es elemento `true`, la omisión de la `DefaultName` (elemento) para los proyectos rellena el cuadro de diálogo con el nombre de la plantilla, es decir, el valor de la [nombre](../extensibility/name-element-visual-studio-templates.md) elemento.
  
## <a name="example"></a>Ejemplo  
 El siguiente ejemplo de código establece la `ProvideDefaultName` elemento `false`.  
  
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
  
## <a name="see-also"></a>Vea también  
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Creación de plantillas de proyecto y elemento](../ide/creating-project-and-item-templates.md)
