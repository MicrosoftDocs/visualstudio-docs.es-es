---
title: Atributos condicionales del esquema XML de VSCT | Microsoft Docs
description: Obtenga información sobre cómo aplicar atributos condicionales a listas y elementos de esquemas XML de VSCT. Los atributos se evalúan como true o false y controlan la salida resultante.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5bc1bcb9d80474b467e90de6262e797087589065
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062361"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>Atributos condicionales del esquema XML de VSCT
Puede aplicar atributos condicionales a todas las listas y elementos. Los operadores lógicos y las expresiones de expansión de símbolos se evalúan como true o false. Si es true, la lista o el elemento asociado se incluye en la salida resultante.

 Puede probar las expansiones de token en otras expansiones o constantes de token. La función `Defined()` comprueba si se ha definido un nombre determinado, incluso si no tiene ningún valor.

 Cuando se aplica un atributo Condition a una lista, la condición se aplica a cada elemento secundario de la lista. Si un elemento secundario contiene un atributo Condition, su condición se combina con la expresión primaria mediante una operación AND.

 Los valores 1, "1" y "true" se evalúan como true, y 0, "0" y "false" se evalúan como false.

## <a name="operators"></a>Operadores
 Utilice los operadores siguientes para evaluar las expresiones condicionales.

|Operator|Definición|
|--------------|----------------|
|(,)|Agrupación|
|!|NOT lógico|
|\<, >, \<=, >=, ==, !=|Relacional e igualdad|
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
- [Tabla de comandos de Visual Studio (. Archivos de Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
