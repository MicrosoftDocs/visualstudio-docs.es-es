---
title: AppliesTo (elemento, plantillas de Visual Studio) | Microsoft Docs
description: Obtenga información sobre el elemento appliesTo y cómo especifica una expresión opcional que coincida con una o más funcionalidades.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 8fb1334b-d78c-405f-98b4-786e9f6b58d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5fca9f6550a066d3f3e0e46514a15d9ff14cb66c
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671706"
---
# <a name="appliesto-element-visual-studio-templates"></a>AppliesTo (elemento, plantillas de Visual Studio)

Especifica una expresión opcional que debe coincidir con una o más capacidades (vea <xref:Microsoft.VisualStudio.Shell.Interop.VsProjectCapabilityExpressionMatcher> ). Los tipos de proyecto exponen las capacidades a través de la jerarquía como una propiedad [__VSHPROPID5. VSHPROPID_ProjectCapabilities](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID5.VSHPROPID_ProjectCapabilities>). De esta manera, la plantilla se puede compartir en varios tipos de proyecto que tengan funciones aplicables comunes.

Este elemento es opcional. Puede haber un máximo de una instancia en un archivo de plantilla. Este elemento solo sirve para designar una plantilla de elemento como aplicable, de acuerdo con las funciones del proyecto activo actualmente seleccionado. No se puede utilizar para designar una plantilla de elemento como no aplicable. Si `AppliesTo` no está presente o la expresión no es capaz de indicar si la plantilla es aplicable, se utiliza `TemplateID` o `TemplateGroupID` para crear la plantilla aplicable, como en las versiones anteriores del producto.

Apareció por primera vez en Visual Studio 2013 Update 2. Para hacer referencia a la versión correcta, consulte la referencia a los [ensamblados proporcionados en la actualización 2 del SDK de Visual Studio 2013](/previous-versions/dn632168(v=vs.120)).

```xml
<VSTemplate>
   <TemplateData>
      <AppliesTo>
```

## <a name="syntax"></a>Sintaxis

```xml
<AppliesTo>Capability1</AppliesTo>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Clasifica la plantilla.|

## <a name="text-value"></a>Valor de texto

Se requiere un valor de texto. Este texto especifica las funciones del proyecto.

La sintaxis de expresión válida se define como:

- La expresión de capacidad, como "(VisualC &#124; CSharp) + (MSTest &#124; NUnit)".

- "&#124;" es el operador OR.

- Los caracteres "&" y "+" son operadores AND.

- El carácter “!” es el operador NOT.

- Los paréntesis indican el orden de prioridad de la evaluación.

- Una expresión null o vacía se evalúa como una coincidencia.

- Las capacidades del proyecto pueden ser cualquier carácter excepto estos caracteres reservados: "' ':;, +-*/ \\ ! ~&#124;&% $ @ ^ () = {} [] <>? \t\b\n\r

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestran tres plantillas diferentes. `Template1` se aplica a todos los tipos de proyecto de C# o a cualquier otro tipo de proyecto que admita la `WindowsAppContainer` funcionalidad. `Template2` se aplica a todos los proyectos de C# de cualquier tipo. `Template3` se aplica a los proyectos de C# que no son proyectos `WindowsAppContainer`.

```xml
<!--  Template 1 -->
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <AppliesTo>CSharp | WindowsAppContainer</AppliesTo>
    </TemplateData>
</VSTemplate>

<!--  Template 2 -->
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <AppliesTo>CSharp</AppliesTo>
    </TemplateData>
</VSTemplate>

<!--  Template 1 -->
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <AppliesTo>CSharp_Class + (!WindowsAppContainer)</AppliesTo>
    </TemplateData>
</VSTemplate>
```

## <a name="see-also"></a>Vea también

- [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Creación de plantillas de proyecto y elemento](../ide/creating-project-and-item-templates.md)
