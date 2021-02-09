---
title: CustomParameters ((elemento, plantillas de Visual Studio) | Microsoft Docs
description: Obtenga información sobre el elemento CustomParameters (y cómo agrupa los parámetros personalizados que se van a pasar al Asistente para plantillas cuando el asistente realiza reemplazos de parámetros.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a899790890bd299dcb77558d31499b0a61bcefe4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927137"
---
# <a name="customparameters-element-visual-studio-templates"></a>CustomParameters ((elemento, plantillas de Visual Studio)
Agrupa los parámetros personalizados que se van a pasar al Asistente para plantillas cuando el asistente realiza reemplazos de parámetros.

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
|[CustomParameter](../extensibility/customparameter-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Contiene un nombre y valor de parámetro personalizado que se usará cuando se cree un proyecto o elemento a partir de la plantilla. Puede haber cero o más elementos `CustomParameter` en un elemento `CustomParameters`.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Especifica el contenido de la plantilla.|

## <a name="remarks"></a>Notas

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra cómo usar varios parámetros personalizados en una plantilla. Cuando se crea un proyecto o un elemento a partir de una plantilla con los siguientes parámetros personalizados, todas las instancias de `$color1$` y `$color2$` de los archivos de plantilla se reemplazarán por `Red` y `Blue` , respectivamente.

```
<CustomParameters>
    <CustomParameter Name="$color1$" Value="Red"/>
    <CustomParameter Name="$color2$" Value="Blue "/>
</CustomParameters>
```

## <a name="see-also"></a>Vea también
- [CustomParameter ((elemento, plantillas de Visual Studio)](../extensibility/customparameter-element-visual-studio-templates.md)
- [Parámetros de plantilla](../ide/template-parameters.md)
- [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
