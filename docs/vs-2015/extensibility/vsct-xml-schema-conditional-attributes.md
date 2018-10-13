---
title: Atributos condicionales de esquema XML de VSCT | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1ee3d25fd7d08ea52c41ef24fdfe654bbf7a2eb2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49246888"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>Atributos condicionales del esquema XML de VSCT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Atributos condicionales se pueden aplicar a todas las listas y elementos. Expresiones de expansión de símbolos y operadores lógicos se evalúan como true o false. Si es true, el elemento o la lista asociada se incluye en la salida resultante.  
  
 Pueden probar las expansiones de token en otras token expansiones o constantes. La función Defined() se usa para comprobar si se ha definido un nombre determinado, incluso si no tiene ningún valor.  
  
 Cuando un atributo Condition se aplica a una lista, la condición se aplica a todos los elementos secundarios en la lista. Si un elemento secundario propio contiene un atributo Condition, su condición se combina con la expresión primaria por una operación de AND.  
  
 Los valores 1, '1' y 'true' se evalúan como true y 0, '0' y 'false' se evalúan como false.  
  
## <a name="operators"></a>Operadores  
 Los siguientes operadores pueden utilizarse para evaluar las expresiones condicionales.  
  
|Operador|de esquema JSON|  
|--------------|----------------|  
|(,)|Agrupar|  
|!|NOT lógico|  
|\<, >, \<=, >=, ==, !=|Relacional e igualdad|  
|y|Booleano|  
|o|Booleano|  
  
## <a name="examples"></a>Ejemplos  
  
```  
<Menu Condition="Defined(DEBUG)" …  
</Menu>  
  
<Menu Condition="%(SKU_MODE) = 'Demo'" …  
</Menu>  
  
<Menus Condition="Defined(DEBUG)">  
    <Menu …  
    </Menu>  
</Menus>  
  
<Menus Condition="Defined(DEMO_SKU)">  
    <Menus Condition="!Defined(DEBUG)">  
        <Menu …  
        </Menu>  
    </Menus>  
  
    <Menu …  
    </Menu>  
</Menus>  
  
<Menus Condition="(Defined(DEMO_SKU) or Defined(SAMPLE_SKU))   
and !Defined(DEBUG)">  
    <Menu …  
    </Menu>  
</Menus>  
```  
  
## <a name="see-also"></a>Vea también  
 [Archivos de tabla de comandos de Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

