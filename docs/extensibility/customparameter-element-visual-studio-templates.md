---
title: Elemento CustomParameter (Plantillas de Visual Studio) Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameter
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: 743c4489-74ac-403a-bbaa-eed7d785a3ac
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9063a354f03b896e189566e8d84a18caf7509db8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739429"
---
# <a name="customparameter-element-visual-studio-templates"></a>Elemento CustomParameter (plantillas de Visual Studio)
Contiene un nombre de parámetro personalizado y un valor para usar cuando se crea un proyecto o elemento a partir de la plantilla.

## <a name="syntax"></a>Sintaxis

```
<CustomParameter Name="name" Value="value">
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|`Name`|Necesario. El nombre del parámetro. El formato de los parámetros es $*name*$.|
|`Value`|Necesario. El valor de reemplazo para el parámetro.|

### <a name="child-elements"></a>Elementos secundarios
 Ninguno.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Agrupa los parámetros personalizados que se van a pasar al asistente de plantilla cuando el asistente realiza reemplazos de parámetros.|

## <a name="remarks"></a>Observaciones
 Cuando una `CustomParameter` plantilla contiene elementos, cada instancia del `Name` atributo se reemplaza por el `Value` atributo en los archivos de proyecto o elemento creados.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra cómo utilizar varios parámetros personalizados en una plantilla. Cuando se crea un proyecto o elemento a partir de `$color1$` una `$color2$` plantilla con los siguientes `Red` parámetros personalizados, todas las instancias de y en los archivos de plantilla se reemplazarán con y `Blue`, respectivamente.

```
<CustomParameters>
    <CustomParameter Name="$color1$" Value="Red"/>
    <CustomParameter Name="$color2$" Value="Blue "/>
</CustomParameters>
```

## <a name="see-also"></a>Vea también
- [Elemento CustomParameters (plantillas de Visual Studio)](../extensibility/customparameters-element-visual-studio-templates.md)
- [Parámetros de plantilla](../ide/template-parameters.md)
- [Referencia de esquema de plantilla de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
