---
title: Elemento Assembly (Plantillas de Visual Studio) Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Assembly
helpviewer_keywords:
- Assembly element [Visual Studio templates]
- <Assembly> element [Visual Studio templates]
ms.assetid: 9242f76a-1273-4b8a-8f26-6606f91829ef
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c80044657b16448ba4567fff839274226985fa14
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740036"
---
# <a name="assembly-element-visual-studio-templates"></a>Elemento Assembly (plantillas de Visual Studio)
Especifica información sobre un ensamblado, que la plantilla utiliza para agregar una referencia de ese ensamblado a los proyectos.

 \<VSTemplate \<> TemplateContent \< \<> \<referencias> referencia> ensamblado>

## <a name="syntax"></a>Sintaxis

```
<Assembly> AssemblyName </Assembly>
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
|[Referencia](../extensibility/reference-element-visual-studio-templates.md)|Especifica la referencia de ensamblado para agregar cuando el elemento se agrega a un proyecto.|

## <a name="text-value"></a>Valor de texto
 Se requiere un valor de texto.

 Este texto especifica el ensamblado que se va a agregar a un proyecto cuando se crea una instancia de la plantilla de elemento. Este nombre de ensamblado debe especificarse de una de las siguientes maneras:

- Como nombre completo del ensamblado. Por ejemplo:

    ```
    <Assembly>
        MyAssembly, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom = null.
    </Assembly>
    ```

- Como referencia de texto simple. Por ejemplo:

    ```
    <Assembly> System </Assembly>
    ```

## <a name="remarks"></a>Observaciones
 `Assembly` es un elemento secundario obligatorio de `Reference`.

 Los `Reference` `References,` elementos , y `Assembly` solo se pueden utilizar `Type` en `Item`archivos *.vstemplate* que tengan un valor de atributo de .

## <a name="example"></a>Ejemplo
 En el ejemplo `TemplateContent` siguiente se muestra el elemento de una plantilla de elemento. Este XML agrega referencias a los ensamblados *System.dll* y *System.Data.dll.*

```
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
- [Referencia de esquema de plantilla de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Crear plantillas de proyecto y elemento](../ide/creating-project-and-item-templates.md)
