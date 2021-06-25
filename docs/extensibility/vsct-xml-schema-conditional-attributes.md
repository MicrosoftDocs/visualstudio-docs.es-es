---
title: Atributos condicionales del esquema XML de VSCT | Microsoft Docs
description: Obtenga información sobre cómo aplicar atributos condicionales a elementos y listas de esquemas XML de VSCT. Los atributos se evalúan como true o false, controlando la salida resultante.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e91207016ed6e1baab80b323680d10a40e0331d8
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905259"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>Atributos condicionales del esquema XML de VSCT
Puede aplicar atributos condicionales a todas las listas y elementos. Los operadores lógicos y las expresiones de expansión de símbolos se evalúan como true o false. Si es true, la lista o elemento asociado se incluye en la salida resultante.

 Puede probar las expansiones de tokens con otras expansiones de tokens o constantes. La función `Defined()` comprueba si se ha definido un nombre determinado, incluso si no tiene ningún valor.

 Cuando se aplica un atributo Condition a una lista, la condición se aplica a todos los elementos secundarios de la lista. Si un elemento secundario contiene un atributo Condition, su condición se combina con la expresión primaria mediante una operación AND.

 Los valores 1, '1' y 'true' se evalúan como true y 0, '0' y 'false' se evalúan como false.

## <a name="operators"></a>Operadores
 Use los operadores siguientes para evaluar expresiones condicionales.

|Operator|Definición|
|--------------|----------------|
|(,)|Agrupar|
|!|NOT lógico|
|\<, >, \<=, >=, ==, !=|Relacional e igualdad|
|y|Booleano|
|or|Booleano|

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
- [Visual Studio tabla de comandos (. Archivos vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
