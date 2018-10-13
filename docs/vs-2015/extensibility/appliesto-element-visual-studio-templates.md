---
title: AppliesTo (elemento) (plantillas de Visual Studio) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8fb1334b-d78c-405f-98b4-786e9f6b58d7
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f7e00fa30d3c2f2b1bfa31152584227bb56639eb
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49218275"
---
# <a name="appliesto-element-visual-studio-templates"></a>AppliesTo (Elemento, Plantillas de Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Especifica una expresión opcional para buscar una o varias funciones coincidentes. (vea <xref:Microsoft.VisualStudio.Shell.Interop.VsProjectCapabilityExpressionMatcher>). Las funciones las exponen los tipos de proyecto a través de la jerarquía como una propiedad <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID5>. De esta manera, la plantilla se puede compartir en varios tipos de proyecto que tengan funciones aplicables comunes.  
  
 Este elemento es opcional. Puede haber un máximo de una instancia en un archivo de plantilla. Este elemento solo sirve para designar una plantilla de elemento como aplicable, de acuerdo con las funciones del proyecto activo actualmente seleccionado. No se puede utilizar para designar una plantilla de elemento como no aplicable. Si `AppliesTo` no está presente o la expresión no es capaz de indicar si la plantilla es aplicable, se utiliza `TemplateID` o `TemplateGroupID` para crear la plantilla aplicable, como en las versiones anteriores del producto.  
  
 Apareció por primera vez en Visual Studio 2013 Update 2. Para hacer referencia a la versión correcta, consulte [que hacen referencia a ensamblados ofrecidas en Visual Studio 2013 SDK Update 2](http://msdn.microsoft.com/en-us/42b65c3e-e42b-4c39-98c8-bea285f25ffb).  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<AppliesTo >  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<AppliesTo>Capability1</AppliesTo>   
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Clasifica la plantilla.|  
  
## <a name="text-value"></a>Valor de texto  
 Se requiere un valor de texto. Este texto especifica las funciones del proyecto.  
  
 La sintaxis de expresión válida se define como:  
  
-   La expresión de la función, como "(VisualC &#124; CSharp) + (MSTest &#124; NUnit)".  
  
-   El "&#124;" es el operador OR.  
  
-   Los caracteres "&" y "+" son operadores AND.  
  
-   El carácter “!” es el operador NOT.  
  
-   Los paréntesis indican el orden de prioridad de la evaluación.  
  
-   Una expresión null o vacía se evalúa como una coincidencia.  
  
-   ¿Las funciones de proyecto pueden ser cualquier carácter salvo estos caracteres reservados: "'' :;,+-*/\\! ~&#124;& %$@^() ={}<> []? \t\b\n\r  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestran tres plantillas diferentes. `Template1` se aplica a todos los tipos de proyecto de C# o a cualquier otro tipo de proyecto que admita la función `WindowsAppContainer`. `Template2` se aplica a todos los proyectos de C# de cualquier tipo. `Template3` se aplica a los proyectos de C# que no son proyectos `WindowsAppContainer`.  
  
```xml  
<!--  Template 1 -->  
<?xml version="1.0" encoding="utf-8"?>  
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <AppliesTo>CSharp | WindowsAppContainer</AppliesTo>   
    </TemplateData>  
</VSTemplate>  
  
<!--  Template 2 -->  
<?xml version="1.0" encoding="utf-8"?>  
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <AppliesTo>CSharp</AppliesTo>   
    </TemplateData>  
</VSTemplate>  
  
<!--  Template 1 -->  
<?xml version="1.0" encoding="utf-8"?>  
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <AppliesTo>CSharp_Class + (!WindowsAppContainer)</AppliesTo>   
    </TemplateData>  
</VSTemplate>  
  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Crear plantillas para proyectos y elementos en Visual Studio](../ide/creating-project-and-item-templates.md)

