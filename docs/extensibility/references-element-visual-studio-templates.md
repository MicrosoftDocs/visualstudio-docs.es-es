---
title: Hace referencia a elemento (plantillas de Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#References
helpviewer_keywords:
- <References> element [Visual Studio Templates]
- References element [Visual Studio Templates]
ms.assetid: 1969146d-46bf-422d-8d46-0e9493925003
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3ae0ee308af1502a7c07766e790b79e51f692a96
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62433414"
---
# <a name="references-element-visual-studio-templates"></a>Elemento References (plantillas de Visual Studio)
Agrupa las referencias de ensamblado que la plantilla se agrega a los proyectos.

 \<VSTemplate > \<TemplateContent > \<referencias >

## <a name="syntax"></a>Sintaxis

```xml
<References>
    <Reference>... </Reference>
    <Reference>... </Reference>
    ...
</References>
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos
 Ninguno.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Referencia](../extensibility/reference-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Especifica la referencia de ensamblado para agregar cuando el elemento se agrega a un proyecto. Debe haber uno o varios `Reference` elementos en un `References` elemento.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Especifica el contenido de la plantilla.|

## <a name="remarks"></a>Comentarios
 `References` es un elemento secundario opcional de `TemplateContent`.

 El `Reference` y `References` elementos solo se pueden utilizar en *.vstemplate* los archivos que tienen un `Type` valor del atributo `Item`.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente ilustra la `TemplateContent` elemento de una plantilla de elemento. Este código XML agrega las referencias a la *System.dll* y *System.Data.dll* ensamblados.

```xml
<TemplateContent>
    <References>
        <Reference>
            <Assembly>
                System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
            </Assembly>
        </Reference>
        <Reference>
            <Assembly>
                System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
            </Assembly>
        </Reference>
    </References>
    ...
</TemplateContent>
```

## <a name="see-also"></a>Vea también
- [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Crear plantillas para proyectos y elementos](../ide/creating-project-and-item-templates.md)
