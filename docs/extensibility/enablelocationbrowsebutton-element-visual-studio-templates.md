---
title: Elemento EnableLocationBrowseButton (Plantillas de Visual Studio) Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#EnableLocationBrowseButton
helpviewer_keywords:
- EnableLocationBrowseButton [Visual Studio project templates]
ms.assetid: a12d10d8-af49-482a-af77-e084fd07a47d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 263157d5c6fefc208f28caa55475ba329a0d230f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711987"
---
# <a name="enablelocationbrowsebutton-element-visual-studio-templates"></a>Elemento EnableLocationBrowseButton (plantillas de Visual Studio)
Especifica si el botón **Examinar** está disponible en el cuadro de diálogo **Nuevo proyecto,** para que los usuarios puedan modificar fácilmente el directorio predeterminado donde se guarda un nuevo proyecto.

 \<VSTemplate \<> TemplateData> \<EnableLocationBrowseButton>

## <a name="syntax"></a>Sintaxis

```
<EnableLocationBrowseButton> true/false </EnableLocationBrowseButton>
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

 El texto debe `true` `false`ser o , que indica si se debe mostrar o no el botón **Examinar** en el cuadro de diálogo **Nuevo proyecto.**

## <a name="remarks"></a>Observaciones
 `EnableLocationBrowseButton` es un elemento opcional. El valor `true`predeterminado es , que muestra el botón **Examinar** en el cuadro de diálogo **Nuevo proyecto.**

 En el cuadro de diálogo **Nuevo proyecto,** el cuadro de texto **Ubicación** especifica el directorio donde se guarda un nuevo proyecto. El botón **Examinar** le ayuda a modificar este directorio mostrando el cuadro de diálogo Ubicación del **proyecto,** que le permite navegar fácilmente a un directorio diferente que está disponible desde el equipo y, a continuación, elegirlo como el directorio donde se guarda el nuevo proyecto.

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
