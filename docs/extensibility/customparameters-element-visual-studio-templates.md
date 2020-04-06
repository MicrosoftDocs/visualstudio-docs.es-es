---
title: Elemento CustomParameters (Plantillas de Visual Studio) Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameters
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: cf3efc91-1532-4022-bbb8-a18658424fee
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f524996c226f001c68ddc7ac9aa8cb3b99857fc5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739411"
---
# <a name="customparameters-element-visual-studio-templates"></a>Elemento CustomParameters (plantillas de Visual Studio)
Agrupa los parámetros personalizados que se van a pasar al asistente de plantilla cuando el asistente realiza reemplazos de parámetros.

## <a name="syntax"></a>Sintaxis

```
<CustomParameters>
    <CustomParameter/>
    <CustomParameter/>
</CustomParameters>
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos
 Ninguno.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[CustomParameter](../extensibility/customparameter-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Contiene un nombre de parámetro personalizado y un valor para usar cuando se crea un proyecto o elemento a partir de la plantilla. Puede haber cero o más elementos `CustomParameter` en un elemento `CustomParameters`.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Especifica el contenido de la plantilla.|

## <a name="remarks"></a>Observaciones

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra cómo utilizar varios parámetros personalizados en una plantilla. Cuando se crea un proyecto o elemento a partir de `$color1$` una `$color2$` plantilla con los siguientes `Red` parámetros personalizados, todas las instancias de y en los archivos de plantilla se reemplazarán con y `Blue`, respectivamente.

```
<CustomParameters>
    <CustomParameter Name="$color1$" Value="Red"/>
    <CustomParameter Name="$color2$" Value="Blue "/>
</CustomParameters>
```

## <a name="see-also"></a>Vea también
- [Elemento CustomParameter (plantillas de Visual Studio)](../extensibility/customparameter-element-visual-studio-templates.md)
- [Parámetros de plantilla](../ide/template-parameters.md)
- [Referencia de esquema de plantilla de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
