---
title: Elemento EnableEditOfLocationField (Plantillas de Visual Studio) Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- EnableEditOfLocationField (Visual Studio project templates)
ms.assetid: 51a91963-8a3f-4741-928e-bc90c11473bb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e15e2f5c070b8a8c565497c6ba3fc6490b87591
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711999"
---
# <a name="enableeditoflocationfield-element-visual-studio-templates"></a>Elemento EnableEditOfLocationField (plantillas de Visual Studio)
Especifica si el usuario puede editar el campo de ubicación.

 \<VSTemplate \<> TemplateData> \<> EnableEditOfLocationField

## <a name="syntax"></a>Sintaxis

```
<EnableEditOfLocationField> true/false </EnableEditOfLocationField>
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos
 None

### <a name="child-elements"></a>Elementos secundarios
 None

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Clasifica la plantilla y define cómo se muestra en el cuadro de diálogo **Nuevo proyecto** o **Agregar nuevo elemento** .|

## <a name="text-value"></a>Valor de texto
 Se requiere un valor de texto.

 El texto debe `true` `false`ser o , que indica si el usuario puede o no editar el cuadro de texto **Ubicación** en el cuadro de diálogo **Nuevo proyecto.**

## <a name="remarks"></a>Observaciones
 `EnableEditOfLocationField` es un elemento opcional. El valor `true`predeterminado es , que permite al usuario editar el valor en el cuadro de texto **Ubicación** del cuadro de diálogo **Nuevo proyecto.**

 En el cuadro de diálogo **Nuevo proyecto,** el cuadro de texto **Ubicación** especifica el directorio donde se guarda un nuevo proyecto.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] muestran los metadatos de una aplicación de Windows.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <EnableEditOfLocationField>false</EnableEditOfLocationField>
        <EnableLocationBrowseButton>false</EnableLocationBrowseButton>
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
- [Creación de plantillas de proyecto y elemento](../ide/creating-project-and-item-templates.md)
