---
title: NumberOfParentCategoriesToRollUp (elemento) (plantillas de Visual Studio)
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#NumberOfParentCategoriesToRollUp
helpviewer_keywords:
- NumberOfParentCategoriesToRollUp element [Visual Studio Templates]
- <NumberOfParentCategoriesToRollUp> element [Visual Studio Templates]
ms.assetid: 6f9d36f5-ae23-4a92-8132-b11799e2c21a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b733b65a62db3cb39197fbdbed4c471651eae49a
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56687953"
---
# <a name="numberofparentcategoriestorollup-element-visual-studio-templates"></a>NumberOfParentCategoriesToRollUp (elemento) (plantillas de Visual Studio)
Especifica el número de categorías primarias que mostrará la plantilla en el **nuevo proyecto** cuadro de diálogo.

 \<VSTemplate> \<TemplateData> \<NumberOfParentCategoriesToRollUp>

## <a name="syntax"></a>Sintaxis

```xml
<NumberOfParentCategoriesToRollUp>
1
</NumberOfParentCategoriesToRollUp>
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
 Un `integer` se requiere un valor.

 Este valor especifica el número de categorías primarias que mostrará la plantilla en el **nuevo proyecto** cuadro de diálogo.

## <a name="remarks"></a>Comentarios
 `NumberOfParentCategoriesToRollUp` es un elemento opcional.

## <a name="example"></a>Ejemplo
 En este ejemplo se muestra los metadatos para un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] aplicación de Windows. Si una plantilla con estos metadatos se coloca dos niveles de carpeta por debajo del nivel superior [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] nodo, la plantilla aparecerá en el nodo de nivel superior en el **nuevo proyecto** cuadro de diálogo. Si el `NumberOfParentCategoriesToRollUp` no está establecido, la plantilla sólo aparece en el nodo en el que está ubicado físicamente.

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <NumberOfParentCategoriesToRollUp>2</NumberOfParentCategoriesToRollUp>
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
- [Crear plantillas para proyectos y elementos](../ide/creating-project-and-item-templates.md)