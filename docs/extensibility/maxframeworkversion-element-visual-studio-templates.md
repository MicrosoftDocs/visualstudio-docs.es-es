---
title: MaxFrameworkVersion (elemento) (plantillas de Visual Studio) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c473b3253809c09f9ba0af90f7a0fed349dedb93
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>MaxFrameworkVersion (Elemento, Plantillas de Visual Studio)
Especifica la versión máxima de .NET Framework que requiere la plantilla. Determina si la plantilla se muestra en el **plantillas** sección de la **Agregar nuevo proyecto** cuadro de diálogo, en función del valor seleccionado en el **deversióndeFrameworkdedestino** cuadro de la **Agregar nuevo proyecto** cuadro de diálogo.  
  
 \<VSTemplate >  
 \<MaxFrameworkVersion >  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<MaxFrameworkVersion> ... </MaxFrameworkVersion>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Clasifica la plantilla y define cómo se muestran en la vista la **nuevo proyecto** o **Agregar nuevo elemento** cuadro de diálogo.|  
  
## <a name="text-value"></a>Valor de texto  
 Se requiere un valor de texto.  
  
 El texto debe ser el mayor número de versión de .NET Framework que está permitido por la plantilla.  
  
## <a name="remarks"></a>Comentarios  
 `MaxFrameworkVersion` es un elemento opcional. El elemento en el `TemplateData` sección del archivo .vstemplate actúa como filtro para el **plantillas** sección de la **Agregar nuevo proyecto** cuadro de diálogo. Sólo las plantillas cuyos requisitos de .NET Framework son menos de `MaxFrameworkVersion` se mostrarán los valores de elemento, en función del valor seleccionado en el **versión de Framework de destino** cuadro de la **Agregar nuevo proyecto**cuadro de diálogo. El `MaxFrameworkVersion` debe omitirse el elemento a menos que sea necesario, para no tener que podrían causar la plantillas de mostrarse cuando se utilizan con las versiones más recientes de .NET Framework.  
  
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
        <MaxFrameworkVersion>3.5</MaxFrameworkVersion>  
        <DefaultName>MyClass</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 En este ejemplo, la versión máxima de .NET Framework que requiere la plantilla, representado por `MaxFrameworkVersion`, es 3.5. Se mostrará la plantilla anterior solo cuando se selecciona 3.0 o 3.5 en el **versión de Framework de destino** cuadro el **Agregar nuevo proyecto** cuadro de diálogo.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Crear plantillas para proyectos y elementos en Visual Studio](../ide/creating-project-and-item-templates.md)