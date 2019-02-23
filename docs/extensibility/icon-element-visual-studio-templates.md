---
title: Icon (elemento) (plantillas de Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Icon
helpviewer_keywords:
- Icon element [Visual Studio project templates]
ms.assetid: ec01d903-f4c2-4ca2-9cbc-e939ec84016c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 623015698ca9855010bf5a4bf5519a780842ffdd
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56717759"
---
# <a name="icon-element-visual-studio-templates"></a>Icon (elemento) (plantillas de Visual Studio)
Especifica la ruta de acceso y el nombre de archivo del archivo de imagen que actúa como el icono, que aparece en cualquiera de los **nuevo proyecto** o el **Agregar nuevo elemento** cuadro de diálogo, para la plantilla.

 \<VSTemplate> \<TemplateData> \<Icon>

## <a name="syntax"></a>Sintaxis

```
<Icon>
    IconFileName
</Icon>
```

```
<Icon Package="{PackageID}" ID="ResourceID" />
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|`Package`|Atributo opcional para escenarios de usuario avanzada.<br /><br /> Identificador de un GUID que especifica el paquete de Visual Studio.|
|`ID`|Atributo opcional para escenarios de usuario avanzada.<br /><br /> Especifica el identificador de recurso de Visual Studio.|

### <a name="child-elements"></a>Elementos secundarios
 Ninguno.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Clasifica la plantilla y define cómo se muestra en el cuadro de diálogo **Nuevo proyecto** o **Agregar nuevo elemento** .|

## <a name="text-value"></a>Valor de texto
 Se requiere un valor de texto a menos que el `Package` y `ID` se usan los atributos.

 El texto proporciona la ruta de acceso y el nombre del icono de la plantilla que va a aparecer en el **nuevo proyecto** cuadro de diálogo.

## <a name="remarks"></a>Comentarios
 `Icon` es un elemento secundario obligatorio de `TemplateData`.

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
- [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Creación de plantillas de proyecto y elemento](../ide/creating-project-and-item-templates.md)