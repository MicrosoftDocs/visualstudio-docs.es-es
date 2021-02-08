---
title: RequiredPlatformVersion (Elemento, Plantillas de Visual Studio)
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d182d308f852dda05f20f4ea30d3536850e20e90
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837026"
---
# <a name="requiredplatformversion-element-visual-studio-templates"></a>RequiredPlatformVersion (elemento, plantillas de Visual Studio)

Especifica la versión mínima del sistema operativo que la plantilla de proyecto necesita para funcionar correctamente. Este elemento se usa para las plantillas de proyecto que crean [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplicaciones.

 El `RequiredPlatformVersion` valor se compara directamente con la versión del sistema operativo. Si el `RequiredPlatformVersion` valor de es mayor que la versión del sistema operativo, la plantilla no aparece en el cuadro de diálogo **nuevo proyecto** . Para especificar una plantilla para [!INCLUDE[win8](../debugger/includes/win8_md.md)] o posterior, establezca `RequiredPlatformVersion` en 6.2.0. Para especificar una plantilla para [!INCLUDE[win81](../debugger/includes/win81_md.md)] o posterior, establezca `RequiredPlatformVersion` en 6.3.0.

 Las plantillas que especifican `RequiredPlatformVersion` = 8 son compatibles con [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] las plantillas de cliente anteriores.

 TemplateData (de VSTemplate..... TargetPlatformName RequiredPlatformVersion

## <a name="syntax"></a>Sintaxis

```xml
<RequiredPlatformVersion> OperatingSystem </RequiredPlatformVersion>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

 Ninguno.

### <a name="attributes"></a>Atributos

 Ninguno.

### <a name="child-elements"></a>Elementos secundarios

 Ninguno.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[TemplatePlatformName](../extensibility/templatedata-element-visual-studio-templates.md)|Especifica la plataforma a la que está orientada la plantilla del proyecto.|

## <a name="text-value"></a>Valor de texto

 Se requiere un valor de texto.

## <a name="remarks"></a>Notas

 Este texto especifica la versión mínima del sistema operativo necesaria para la plantilla.

## <a name="example"></a>Ejemplo

 Este ejemplo especifica que la plantilla del proyecto está orientada a [!INCLUDE[win8](../debugger/includes/win8_md.md)] o posterior.

```xml
<VSTemplate Type="Project" Version="3.0.0"    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <TargetPlatformName>Windows</TargetPlatformName>
            <RequiredPlatformVersion>6.3.0</RequiredPlatformVersion>

    </TemplateData>
    <TemplateContent>

    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Vea también

- [TargetPlatformName (elemento, plantillas de Visual Studio)](../extensibility/targetplatformname-element-visual-studio-templates.md)
- [Creación de plantillas de proyecto y elemento](../ide/creating-project-and-item-templates.md)
- [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
