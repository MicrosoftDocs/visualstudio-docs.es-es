---
title: Atributos condicionales del esquema XML de VSCT | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80697945"
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
|(,)|Agrupar|
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
