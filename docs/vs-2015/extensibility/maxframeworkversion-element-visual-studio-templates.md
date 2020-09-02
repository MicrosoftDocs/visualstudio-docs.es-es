---
title: MaxFrameworkVersion (elemento, plantillas de Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4a1c27e42574429dbb6b2eaeb140db484bf29db5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194329"
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>MaxFrameworkVersion (Elemento, Plantillas de Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Especifica la versión máxima del .NET Framework que requiere la plantilla. Determina si la plantilla se muestra en la sección **plantillas** del cuadro de diálogo **Agregar nuevo proyecto** , en función del valor seleccionado en el cuadro versión de **.NET Framework de destino** del cuadro de diálogo **Agregar nuevo proyecto** .  
  
 \<VSTemplate>  
 \<MaxFrameworkVersion>  
  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Clasifica la plantilla y define cómo se muestra en el cuadro de diálogo **nuevo proyecto** o **Agregar nuevo elemento** .|  
  
## <a name="text-value"></a>Valor de texto  
 Se requiere un valor de texto.  
  
 El texto debe ser el número de versión más alto del .NET Framework permitido por la plantilla.  
  
## <a name="remarks"></a>Comentarios  
 `MaxFrameworkVersion` es un elemento opcional. El elemento de la `TemplateData` sección del archivo. vstemplate actúa como un filtro para la sección **plantillas** del cuadro de diálogo **Agregar nuevo proyecto** . Solo se mostrarán las plantillas cuyos requisitos de .NET Framework sean inferiores a `MaxFrameworkVersion` los valores de elemento, según el valor seleccionado en el cuadro **versión de .NET Framework de destino** del cuadro de diálogo **Agregar nuevo proyecto** . Se `MaxFrameworkVersion` debe omitir el elemento a menos que sea necesario, por lo que no se puede hacer que las plantillas se muestren sin darse cuenta cuando se usan con las versiones más recientes del .NET Framework.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestran los metadatos de una [!INCLUDE[csprcs](../includes/csprcs-md.md)] plantilla de clase estándar.  
  
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
  
 En este ejemplo, la versión máxima de la .NET Framework requerida por la plantilla, representada por `MaxFrameworkVersion` , es 3,5. La plantilla anterior solo se mostrará cuando seleccione 3,0 o 3,5 en el cuadro versión de **.NET Framework de destino** en el cuadro de diálogo **Agregar nuevo proyecto** .  
  
## <a name="see-also"></a>Consulte también  
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Crear plantillas de proyecto y de elemento](../ide/creating-project-and-item-templates.md)
