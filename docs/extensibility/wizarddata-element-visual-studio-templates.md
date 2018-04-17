---
title: WizardData (elemento) (plantillas de Visual Studio) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#WizardData
helpviewer_keywords:
- WizardData element [Visual Studio Templates]
- <WizardData> element [Visual Studio Templates]
ms.assetid: d0403a16-5d07-4fe5-b474-19ae3d9fd3ab
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6685c09e463b50f1fd856c65eadc09555a6dedb9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="wizarddata-element-visual-studio-templates"></a>WizardData (Elemento, Plantillas de Visual Studio)
Especifica el código XML personalizado  
  
 \<VSTemplate >  
 \<WizardData >  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<WizardData>  
    <!-- XML to pass to the custom wizard extension -->  
    ...  
</WizardData>  
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
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Contiene todos los metadatos de la plantilla de proyecto, una plantilla de elemento o un kit de inicio.|  
  
## <a name="text-value"></a>Valor de texto  
 El valor de texto es opcional.  
  
 Este texto especifica el código XML personalizado para pasar a la extensión de asistente personalizada especificada en el [WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md) elemento.  
  
## <a name="remarks"></a>Comentarios  
 Cualquier XML puede especificarse en este elemento. El código XML se pasarán como un parámetro a la extensión de asistente personalizada, permitiendo a la extensión usar el contenido de este elemento. Se realiza ninguna validación en estos datos.  
  
 El contenido de la `WizardData` elemento se pasa sin cambios, como un parámetro en el diccionario de cadenas de parámetros en el `IWizard.RunStarted` método. El parámetro se denomina $WizardData$.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra los metadatos de la plantilla de proyecto estándar para un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] aplicación de Windows.  
  
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
            <ProjectItem>Form1.cs<ProjectItem>  
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
        <Assembly>MyWizard, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom=null</Assembly>  
        <FullClassName>MyWizard.CustomWizard</FullClassName>  
    </WizardExtension>  
    <WizardData>  
        <!-- XML to pass to the custom wizard extension -->  
    </WizardData>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Crear plantillas para proyectos y elementos en Visual Studio](../ide/creating-project-and-item-templates.md)   
 [WizardExtension (elemento) (plantillas de Visual Studio)](../extensibility/wizardextension-element-visual-studio-templates.md)   
 [Uso de asistentes con las plantillas de proyectos](../extensibility/how-to-use-wizards-with-project-templates.md)