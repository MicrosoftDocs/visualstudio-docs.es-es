---
title: Elemento Descripción (Plantillas de Visual Studio) Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Description element [Visual Studio project templates]
ms.assetid: 6e12be73-081f-4c7d-898f-027c307a9fe1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2ea10b43662d2818792dbc57aeac09a056cb63ce
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712259"
---
# <a name="description-element-visual-studio-templates"></a>Elemento Description (plantillas de Visual Studio)
Especifica la descripción de la plantilla tal como aparece en el cuadro de diálogo **Nuevo proyecto** o Agregar **nuevo elemento.**

 \<DESCRIPción \<de la \<> de templateData> de VSTemplate>

## <a name="syntax"></a>Sintaxis

```
<Description>
    Template Description
</Description>
```

```
<Description Package="{PackageID}" ID="ResourceID" />
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|`Package`|Atributo opcional, para escenarios de usuario avanzados.<br /><br /> Un identificador GUID que especifica el id. paquete de Visual Studio.|
|`ID`|Atributo opcional, para escenarios de usuario avanzados.<br /><br /> Especifica el identificador de recurso de Visual Studio.|

### <a name="child-elements"></a>Elementos secundarios
 Ninguno.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Clasifica la plantilla y define cómo se muestra en el cuadro de diálogo **Nuevo proyecto** o **Agregar nuevo elemento** .|

## <a name="text-value"></a>Valor de texto
 Se requiere un valor de texto a menos que se usen los atributos `Package` y `ID`.

 El texto proporciona una descripción de la plantilla.

## <a name="remarks"></a>Observaciones
 `Description`es un elemento secundario `TemplateData` necesario del elemento.

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
- [Creación de plantillas de proyecto y elemento](../ide/creating-project-and-item-templates.md)
