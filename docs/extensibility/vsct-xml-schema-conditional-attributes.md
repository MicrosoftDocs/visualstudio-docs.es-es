---
title: Atributos condicionales del esquema XML de VSCT ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f2b1fb3ee1b2cd396f25ec5591a585f8d87648d0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697945"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>Atributos condicionales de esquema XML de VSCT
Puede aplicar atributos condicionales a todas las listas y elementos. Los operadores lógicos y las expresiones de expansión de símbolos se evalúan como true o false. Si es true, la lista o el elemento asociado se incluye en la salida resultante.

 Puede probar expansiones de tokens con otras expansiones o constantes de token. La `Defined()` función comprueba si se ha definido un nombre determinado, incluso si no tiene ningún valor.

 Cuando se aplica un atributo Condition a una lista, la condición se aplica a todos los elementos secundarios de la lista. Si un elemento secundario contiene un atributo Condition, su condición se combina con la expresión primaria mediante una operación AND.

 Los valores 1, '1' y 'true' se evalúan como true, y 0, '0' y 'false' se evalúan como false.

## <a name="operators"></a>Operadores
 Utilice los siguientes operadores para evaluar expresiones condicionales.

|Operator|Definición|
|--------------|----------------|
|(,)|Agrupación|
|!|NOT lógico|
|\<, >, \<>, ,, !, !, , , , , , , , , , , , , , , , , , , , , , , , , , , , , , ,|Relacional e igualdad|
|y|Boolean|
|or|Boolean|

## <a name="examples"></a>Ejemplos

```xml
<Menu Condition="Defined(DEBUG)" ...
</Menu>

<Menu Condition="%(SKU_MODE) = 'Demo'" ...
</Menu>

<Menus Condition="Defined(DEBUG)">
    <Menu ...
    </Menu>
</Menus>

<Menus Condition="Defined(DEMO_SKU)">
    <Menus Condition="!Defined(DEBUG)">
        <Menu ...
        </Menu>
    </Menus>

    <Menu ...
    </Menu>
</Menus>

<Menus Condition="(Defined(DEMO_SKU) or Defined(SAMPLE_SKU))
and !Defined(DEBUG)">
    <Menu ...
    </Menu>
</Menus>
```

## <a name="see-also"></a>Vea también
- [Tabla de comandos de Visual Studio (. Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
