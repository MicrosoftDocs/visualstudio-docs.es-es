---
title: ProjectType (elemento) (plantillas de Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectType
helpviewer_keywords:
- ProjectType element [Visual Studio project templates]
ms.assetid: ccf9d83f-c7f3-49c7-a31f-e1f22bec004c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d66af0c4ce83feb1153cfd53bf12d8ae40f38b69
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/26/2019
ms.locfileid: "55071012"
---
# <a name="projecttype-element-visual-studio-templates"></a>ProjectType (elemento) (plantillas de Visual Studio)
Clasifica la plantilla de proyecto para que aparezca en el grupo especificado en el **nuevo proyecto** o **Agregar nuevo elemento** cuadro de diálogo.  
  
> [!WARNING]
>  Se admiten las plantillas de proyecto de C++ a partir de Visual Studio 2012. No se admiten para C++ en Visual Studio 2010 y versiones anteriores.  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<ProjectType>  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
<ProjectType> CSharp/VisualBasic/VC/Web </ProjectType>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Clasifica la plantilla y define cómo se muestra en el cuadro de diálogo **Nuevo proyecto** o **Agregar nuevo elemento** .|  
  
## <a name="text-value"></a>Valor de texto  
 Se requiere un valor de texto.  
  
 Este valor especifica el tipo de la plantilla de proyecto se creará y debe contener uno de los siguientes valores:  
  
- `CSharp`: Especifica que la plantilla crea un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] proyecto o elemento.  
  
- `VisualBasic`: Especifica que la plantilla crea un [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] proyecto o elemento.  
  
- `Web`: Especifica que la plantilla crea un proyecto o elemento Web. Si el `ProjectType` elemento contiene este valor, el lenguaje del proyecto o elemento se define en el [ProjectSubType Element (Visual Studio Templates)](../extensibility/projectsubtype-element-visual-studio-templates.md).  
  
## <a name="remarks"></a>Comentarios  
 `ProjectType` es un elemento secundario obligatorio de `TemplateData`.  
  
 El valor de la `ProjectType` elemento especifica dónde se encuentra la plantilla en el **nuevo proyecto** o **Agregar nuevo elemento** cuadro de diálogo. Por ejemplo, una plantilla con un `ProjectType` valor de `CSharp` aparece bajo el **Visual C#** nodo en el **nuevo proyecto** cuadro de diálogo.  
  
 Un subtipo de la plantilla puede especificarse mediante la [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) elemento.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra los metadatos para una plantilla de proyecto para un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] aplicación.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyStarterKit.csproj">  
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
</VSTemplate>  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Crear plantillas de proyecto y elemento](../ide/creating-project-and-item-templates.md)   
 [ProjectSubType (elemento) (plantillas de Visual Studio)](../extensibility/projectsubtype-element-visual-studio-templates.md)