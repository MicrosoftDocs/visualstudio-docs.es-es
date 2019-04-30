---
title: Hacer referencia a elemento (plantillas de Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Reference
helpviewer_keywords:
- Reference element [Visual Studio templates]
- <Reference> element [Visual Studio templates]
ms.assetid: 852772ea-c324-42e9-8c8a-6d565414a109
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0c04f644a102af43682bd7bc7569d35f0d5eeacd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62805911"
---
# <a name="reference-element-visual-studio-templates"></a>Elemento de referencia (plantillas de Visual Studio)
Especifica la referencia de ensamblado para agregar cuando el elemento se agrega a un proyecto.

 \<VSTemplate > \<TemplateContent > \<referencias > \<referencia >

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
|[Ensamblado](../extensibility/assembly-element-visual-studio-templates.md)|Elemento necesario.<br /><br /> Especifica información sobre un ensamblado, que usa la plantilla para agregar una referencia de ensamblado a los proyectos. Debe haber una `Assembly` elemento en cada `Reference` elemento.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Referencias](../extensibility/references-element-visual-studio-templates.md)|Agrupa las referencias de ensamblado que la plantilla se agrega a los proyectos.|

## <a name="remarks"></a>Comentarios
 `Reference` es un elemento secundario obligatorio de `References`.

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
- [Creación de plantillas de proyecto y elemento](../ide/creating-project-and-item-templates.md)
