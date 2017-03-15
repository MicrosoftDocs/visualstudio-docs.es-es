---
title: "Atributos condicionales de esquema XML VSCT | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Elementos de esquema XML VSCT, atributos condicionales"
  - "atributos condicionales (esquema VSCT XML)"
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# Atributos condicionales de esquema XML VSCT
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Atributos condicionales pueden aplicarse a todas las listas y elementos. Expresiones de expansión de símbolos y operadores lógicos se evalúan como true o false. Si es true, el elemento o la lista asociada se incluye en la salida resultante.  
  
 Token expansiones se pueden probar con otros tokens expansiones o constantes. La función Defined\(\) se usa para comprobar si se ha definido un nombre determinado, incluso si no tiene ningún valor.  
  
 Cuando se aplica un atributo de condición para una lista, la condición se aplica a todos los elementos secundarios en la lista. Si un elemento secundario contiene un atributo Condition, su condición se combina con la expresión primaria por una operación AND.  
  
 Los valores 1, '1' y 'true' se evalúan como true y 0, '0' y 'false' se evalúan como false.  
  
## Operadores  
 Los siguientes operadores pueden utilizarse para evaluar expresiones condicionales.  
  
|Operador|Definición|  
|--------------|----------------|  
|\(,\)|Agrupar|  
|\!|NOT lógico|  
|\<, \>, \<\=, \>\=, \=\=, \!\=|Relacional e igualdad|  
|y|Booleano|  
|o|Booleano|  
  
## Ejemplos  
  
```  
<Menu Condition="Defined(DEBUG)" … </Menu> <Menu Condition="%(SKU_MODE) = 'Demo'" … </Menu> <Menus Condition="Defined(DEBUG)"> <Menu … </Menu> </Menus> <Menus Condition="Defined(DEMO_SKU)"> <Menus Condition="!Defined(DEBUG)"> <Menu … </Menu> </Menus> <Menu … </Menu> </Menus> <Menus Condition="(Defined(DEMO_SKU) or Defined(SAMPLE_SKU)) and !Defined(DEBUG)"> <Menu … </Menu> </Menus>  
```  
  
## Vea también  
 [Tabla de comandos de Visual Studio \(. Archivos de Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)