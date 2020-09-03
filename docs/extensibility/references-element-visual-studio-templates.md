---
title: References (elemento, plantillas de Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#References
helpviewer_keywords:
- <References> element [Visual Studio Templates]
- References element [Visual Studio Templates]
ms.assetid: 1969146d-46bf-422d-8d46-0e9493925003
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ef31c5e7550ec7c6e4570d156d364afcf4ad6819
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701612"
---
# <a name="references-element-visual-studio-templates"></a>References (elemento, plantillas de Visual Studio)
Agrupa las referencias de ensamblado que la plantilla agrega a los proyectos.

 \<VSTemplate> \<TemplateContent>
 \<References>

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

## <a name="remarks"></a>Observaciones
 `References` es un elemento secundario opcional de `TemplateContent`.

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
- [Crear plantillas para proyectos y elementos](../ide/creating-project-and-item-templates.md)
