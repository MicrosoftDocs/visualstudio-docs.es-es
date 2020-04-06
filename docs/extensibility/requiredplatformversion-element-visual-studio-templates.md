---
title: Elemento RequiredPlatformVersion (Plantillas de Visual Studio) Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3bc22f97401fe5e3724f2e44c873c72acbf65be1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701497"
---
# <a name="requiredplatformversion-element-visual-studio-templates"></a>Elemento RequiredPlatformVersion (plantillas de Visual Studio)
Especifica la versión mínima del sistema operativo que la plantilla de proyecto requiere para funcionar correctamente. Este elemento se utiliza para [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] las plantillas de proyecto que crean aplicaciones.

 El `RequiredPlatformVersion` valor se compara directamente con la versión del sistema operativo. Si `RequiredPlatformVersion` la versión del sistema operativo es superior a la del sistema operativo, la plantilla no aparece en el cuadro de diálogo **Nuevo proyecto.** Para especificar una [!INCLUDE[win8](../debugger/includes/win8_md.md)] plantilla para `RequiredPlatformVersion` o superior, establezca en 6.2.0. Para especificar una [!INCLUDE[win81](../debugger/includes/win81_md.md)] plantilla para `RequiredPlatformVersion` o superior, establezca en 6.3.0.

 Las plantillas `RequiredPlatformVersion`que especifican el [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] número 8 son compatibles con las plantillas de cliente anteriores.

 VSTemplate TemplateData ..... TargetPlatformName RequiredPlatformVersion

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

## <a name="remarks"></a>Observaciones
 Este texto especifica la versión mínima del sistema operativo requerida por la plantilla.

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
- [Elemento TargetPlatformName (plantillas de Visual Studio)](../extensibility/targetplatformname-element-visual-studio-templates.md)
- [Crear plantillas de proyecto y elemento](../ide/creating-project-and-item-templates.md)
- [Referencia de esquema de plantilla de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
