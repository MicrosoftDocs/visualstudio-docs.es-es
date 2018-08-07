---
title: Atributos condicionales de esquema XML de VSCT | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b31b99e38eeec2ff1e5e31bc6bdaeed3d3be3d83
ms.sourcegitcommit: 56ae5032d99d948aae0548ae318ca2bae97ea962
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2018
ms.locfileid: "39586826"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>Atributos condicionales de esquema XML de VSCT
Puede aplicar atributos condicionales para todas las listas y elementos. Expresiones de expansión de símbolos y operadores lógicos se evalúan como true o false. Si es true, el elemento o la lista asociada se incluye en la salida resultante.  
  
 Puede probar el token expansiones frente a otros tokens expansiones o constantes. La función `Defined()` comprueba si se ha definido un nombre determinado, incluso si no tiene ningún valor.  
  
 Cuando un atributo Condition se aplica a una lista, la condición se aplica a todos los elementos secundarios en la lista. Si un elemento secundario propio contiene un atributo Condition, su condición se combina con la expresión primaria por una operación de AND.  
  
 Los valores 1, '1' y 'true' se evalúan como true y 0, '0' y 'false' se evalúan como false.  
  
## <a name="operators"></a>Operadores  
 Utilice los siguientes operadores para evaluar expresiones condicionales.  
  
|Operador|de esquema JSON|  
|--------------|----------------|  
|(,)|Agrupar|  
|!|NOT lógico|  
|\<, >, \<=, >=, ==, !=|Relacional e igualdad|  
|y|Booleano|  
|o|Booleano|  
  
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
 [Tabla de comandos de Visual Studio (. Archivos Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)