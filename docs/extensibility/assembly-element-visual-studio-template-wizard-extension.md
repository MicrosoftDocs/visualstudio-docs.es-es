---
title: Elemento Assembly (extensión de Asistente de plantilla de Visual Studio) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Assembly
helpviewer_keywords:
- Assembly element [Visual Studio Template Wizard Extension]
- <Assembly> element [Visual Studio Template Wizard Extension]
ms.assetid: 0c3dc280-1753-4ea2-a13c-d31d13b935b2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9fa0728be191086ba84de86110deea122316466f
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/19/2018
ms.locfileid: "39153862"
---
# <a name="assembly-element-visual-studio-template-wizard-extension"></a>Elemento Assembly (extensión de Asistente de plantilla de Visual Studio)
Especifica el nombre o el nombre seguro del ensamblado que implementa el `IWizard` interfaz.  
  
 \<VSTemplate >  
\<WizardExtension >  
\<Ensamblado >  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<Assembly>AssemblyName</Assembly>  
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
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|Contiene los elementos de registro para personalizar al Asistente para la plantilla.|  
  
## <a name="text-value"></a>Valor de texto  
 Se requiere un valor de texto.  
  
 Este texto especifica el ensamblado que implementa el `IWizard` interfaz. Este nombre de ensamblado debe especificarse como un nombre completo del ensamblado. Por ejemplo: `MyAssembly, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11dd0a3a, Custom = null`.  
  
## <a name="remarks"></a>Comentarios  
 `Assembly` es un elemento secundario obligatorio de `WizardExtension`.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra los metadatos de la plantilla de proyecto estándar para un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] aplicación de Windows.  
  
```  
<VSTemplate Version="3.0.0" Type="Item"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyTemplate</Name>  
        <Description>Template using IWizard extension</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyTemplate.csproj">  
            <ProjectItem>Form1.cs</ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>  
            <ProjectItem>Properties\Resources.resx</ProjectItem>  
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>  
            <ProjectItem>Properties\Settings.settings</ProjectItem>  
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
    <WizardExtension>  
        <Assembly>MyWizard, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11dd0a3a, Custom=null</Assembly>  
        <FullClassName>MyWizard.CustomWizard</FullClassName>  
    </WizardExtension>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Creación de plantillas de proyecto y elemento](../ide/creating-project-and-item-templates.md)   
 [Cómo: usar asistentes con plantillas de proyecto](../extensibility/how-to-use-wizards-with-project-templates.md)