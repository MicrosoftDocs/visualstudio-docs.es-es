---
title: ProjectType (elemento, plantillas de Visual Studio) | Microsoft Docs
description: Obtenga información sobre el elemento ProjectType y cómo clasifica la plantilla de proyecto para que aparezca en el cuadro de diálogo nuevo proyecto o agregar nuevo elemento.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectType
helpviewer_keywords:
- ProjectType element [Visual Studio project templates]
ms.assetid: ccf9d83f-c7f3-49c7-a31f-e1f22bec004c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a90c8de2fca62ef303ce8055993d8e2f6d230493
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910888"
---
# <a name="projecttype-element-visual-studio-templates"></a>ProjectType (elemento, plantillas de Visual Studio)
Clasifica la plantilla de proyecto para que aparezca bajo el grupo especificado en el cuadro de diálogo **nuevo proyecto** o **Agregar nuevo elemento** .

> [!WARNING]
> Las plantillas de proyecto son compatibles con C++ a partir de Visual Studio 2012. No se admiten para C++ en Visual Studio 2010 y versiones anteriores.

 \<VSTemplate> \<TemplateData>
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

 Este valor especifica el tipo de proyecto que creará la plantilla y debe contener uno de los valores siguientes:

- `CSharp`: Especifica que la plantilla crea un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] proyecto o un elemento.

- `VisualBasic`: Especifica que la plantilla crea un [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] proyecto o un elemento.

- `Web`: Especifica que la plantilla crea un proyecto o un elemento Web. Si el `ProjectType` elemento contiene este valor, el lenguaje del proyecto o elemento se define en el [elemento ProjectSubType (plantillas de Visual Studio)](../extensibility/projectsubtype-element-visual-studio-templates.md).

## <a name="remarks"></a>Notas
 `ProjectType` es un elemento secundario obligatorio de `TemplateData`.

 El valor del `ProjectType` elemento especifica dónde se encuentra la plantilla en el cuadro de diálogo **nuevo proyecto** o **Agregar nuevo elemento** . Por ejemplo, una plantilla con un `ProjectType` valor de `CSharp` aparece bajo el nodo **Visual C#** en el cuadro de diálogo **nuevo proyecto** .

 Un subtipo de plantilla se puede especificar mediante el elemento [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) .

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestran los metadatos de una plantilla de proyecto para una [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] aplicación.

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
- [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Creación de plantillas de proyecto y elemento](../ide/creating-project-and-item-templates.md)
- [ProjectSubType (elemento, plantillas de Visual Studio)](../extensibility/projectsubtype-element-visual-studio-templates.md)
