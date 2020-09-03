---
title: Elemento Locationfield ((plantillas de proyecto de Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
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
ms.openlocfilehash: 8a5f2f47eef9c3cb047b5550e466585ef70e8f4e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85770024"
---
# <a name="locationfield-element-visual-studio-project-templates"></a>Locationfield ((elemento, plantillas de proyecto de Visual Studio)
Especifica si el cuadro de texto **Ubicación** del cuadro de diálogo **nuevo proyecto** está habilitado, deshabilitado u oculto para la plantilla de proyecto.

 \<VSTemplate> \<TemplateData>
 \<LocationField>

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Clasifica la plantilla y define cómo se muestra en el **nuevo proyecto**.|

## <a name="text-value"></a>Valor de texto
 Se requiere un valor de texto.

 Los valores de texto válidos son:

- `Enabled`, que especifica que el cuadro **Ubicación** del cuadro de diálogo **nuevo proyecto** está habilitado.

- `Disabled`, que especifica que el cuadro **Ubicación** del cuadro de diálogo **nuevo proyecto** está deshabilitado.

- `Hidden`, que especifica que el cuadro **Ubicación** del cuadro de diálogo **nuevo proyecto** está oculto.

## <a name="remarks"></a>Observaciones
 El valor predeterminado es `Enabled`.

 El cuadro de texto **Ubicación** del cuadro de diálogo **nuevo proyecto** permite a los usuarios cambiar el directorio predeterminado en el que se guardan los nuevos proyectos.

 El valor especificado en el `Location` elemento solo lo respeta el cuadro de diálogo si el sistema del proyecto subyacente lo admite.

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
- [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Crear plantillas para proyectos y elementos](../ide/creating-project-and-item-templates.md)
