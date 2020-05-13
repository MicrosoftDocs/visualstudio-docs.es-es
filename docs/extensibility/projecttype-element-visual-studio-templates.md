---
title: Elemento ProjectType (Plantillas de Visual Studio) Microsoft Docs
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d794bd5e81e77a892b5a3be38ff73ab805582dd7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701810"
---
# <a name="projecttype-element-visual-studio-templates"></a>Elemento ProjectType (plantillas de Visual Studio)
Categoriza la plantilla de proyecto para que aparezca bajo el grupo especificado en el cuadro de diálogo **Nuevo proyecto** o Agregar **nuevo elemento.**

> [!WARNING]
> Las plantillas de proyecto se admiten para C++ a partir de Visual Studio 2012. No se admiten para C++ en Visual Studio 2010 y versiones anteriores.

 \<VSTemplate \<> TemplateData> \<projectType>

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

 Este valor especifica el tipo de proyecto que creará la plantilla y debe contener uno de los siguientes valores:

- `CSharp`: especifica que la [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] plantilla crea un proyecto o elemento.

- `VisualBasic`: especifica que la [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] plantilla crea un proyecto o elemento.

- `Web`: especifica que la plantilla crea un proyecto web o un elemento. Si `ProjectType` el elemento contiene este valor, el idioma del proyecto o elemento se define en el [elemento ProjectSubType (plantillas](../extensibility/projectsubtype-element-visual-studio-templates.md)de Visual Studio) .

## <a name="remarks"></a>Observaciones
 `ProjectType` es un elemento secundario obligatorio de `TemplateData`.

 El valor `ProjectType` del elemento especifica dónde se encuentra la plantilla en el cuadro de diálogo **Nuevo proyecto** o **Agregar nuevo elemento.** Por ejemplo, una `ProjectType` plantilla `CSharp` con un valor de aparece en el nodo **Visual C.** en el cuadro de diálogo **Nuevo proyecto.**

 Se puede especificar un subtipo de plantilla mediante el elemento [ProjectSubType.](../extensibility/projectsubtype-element-visual-studio-templates.md)

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestran [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] los metadatos de una plantilla de proyecto para una aplicación.

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
- [Referencia de esquema de plantilla de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Crear plantillas de proyecto y elemento](../ide/creating-project-and-item-templates.md)
- [Elemento ProjectSubType (plantillas de Visual Studio)](../extensibility/projectsubtype-element-visual-studio-templates.md)
