---
title: Reference (elemento, plantillas de Visual Studio) | Microsoft Docs
description: Obtenga información sobre el elemento Reference y cómo especifica la referencia de ensamblado que se va a agregar cuando el elemento se agregue a un proyecto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Reference
helpviewer_keywords:
- Reference element [Visual Studio templates]
- <Reference> element [Visual Studio templates]
ms.assetid: 852772ea-c324-42e9-8c8a-6d565414a109
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5c000a8d11f958daa1c7c8717dc4f18365e0a147
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914986"
---
# <a name="reference-element-visual-studio-templates"></a>Reference (elemento, plantillas de Visual Studio)
Especifica la referencia de ensamblado para agregar cuando el elemento se agrega a un proyecto.

 \<VSTemplate> \<TemplateContent>
 \<References>
 \<Reference>

## <a name="syntax"></a>Sintaxis

```xml
<Reference>
    <Assembly> ... </Assembly>
</Reference>
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos
 Ninguno.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Ensamblaje](../extensibility/assembly-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Especifica información sobre un ensamblado, que la plantilla utiliza para agregar una referencia de ese ensamblado a los proyectos. Debe haber un `Assembly` elemento en cada `Reference` elemento.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Referencias](../extensibility/references-element-visual-studio-templates.md)|Agrupa las referencias de ensamblado que la plantilla agrega a los proyectos.|

## <a name="remarks"></a>Notas
 `Reference` es un elemento secundario obligatorio de `References`.

 Los `Reference` `References` elementos y solo se pueden usar en los archivos *. vstemplate* que tienen un `Type` valor de atributo de `Item` .

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra el `TemplateContent` elemento de una plantilla de elemento. Este XML agrega referencias a los ensamblados de *System.dll* y *System.Data.dll* .

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
- [Creación de plantillas de proyecto y elemento](../ide/creating-project-and-item-templates.md)
