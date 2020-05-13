---
title: Elemento LocationField (Plantillas de proyecto de Visual Studio) Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#LocationField
helpviewer_keywords:
- LocationField element [Visual Studio project templates]
ms.assetid: 6aaaa155-6ce0-4f7f-aa50-8d63d7a7c992
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d993e84bec41486ef4dce6ad98c61f23ab2a46bd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702882"
---
# <a name="locationfield-element-visual-studio-project-templates"></a>Elemento LocationField (plantillas de proyecto de Visual Studio)
Especifica si el cuadro de texto **Ubicación** del cuadro de diálogo **Nuevo proyecto** está habilitado, deshabilitado u oculto para la plantilla de proyecto.

 \<VSTemplate \<> TemplateData> \<> de LocationField

## <a name="syntax"></a>Sintaxis

```
<LocationField> Enabled/Disabled/Hidden </LocationField>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Categoriza la plantilla y define cómo se muestra en el **nuevo proyecto**.|

## <a name="text-value"></a>Valor de texto
 Se requiere un valor de texto.

 Los valores de texto válidos son:

- `Enabled`, que especifica que el cuadro **Ubicación** del cuadro de diálogo **Nuevo proyecto** está habilitado.

- `Disabled`, que especifica que el cuadro **Ubicación** del cuadro de diálogo **Nuevo proyecto** está deshabilitado.

- `Hidden`, que especifica que el cuadro **Ubicación** del cuadro de diálogo **Nuevo proyecto** está oculto.

## <a name="remarks"></a>Observaciones
 El valor predeterminado es `Enabled`.

 El cuadro de texto **Ubicación** del cuadro de diálogo **Nuevo proyecto** permite a los usuarios cambiar el directorio predeterminado en el que se guardan los nuevos proyectos.

 El valor especificado `Location` en el elemento solo lo respeta el cuadro de diálogo si el sistema de proyecto subyacente lo admite.

## <a name="example"></a>Ejemplo
 En el siguiente ejemplo se muestran los metadatos de una plantilla de [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]:

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <LocationField>Disabled</LocationField>
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
</VSTemplate>
```

## <a name="see-also"></a>Vea también
- [Referencia de esquema de plantilla de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Creación de plantillas de proyecto y elemento](../ide/creating-project-and-item-templates.md)
