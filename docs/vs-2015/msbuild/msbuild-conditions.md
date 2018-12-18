---
title: Condiciones de MSBuild | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, conditions
- conditions [MSBuild]
ms.assetid: 9d7aa308-b667-48ed-b4c9-a61e49eb0a85
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba55fca6e34cb93af257f32f33df7b7b8c6d6045
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49286317"
---
# <a name="msbuild-conditions"></a>Condiciones de MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] admite un conjunto específico de condiciones que se pueden aplicar allí donde se permita un atributo `Condition`. En la siguiente tabla se explican esas condiciones.  
  
|Condición|Descripción|  
|---------------|-----------------|  
|'`stringA`' == '`stringB`'|Se evalúa como `true` si `stringA` es igual a `stringB`.<br /><br /> Por ejemplo:<br /><br /> `Condition="'$(CONFIG)'=='DEBUG'"`<br /><br /> Las comillas simples no son necesarias para las cadenas alfanuméricas simples o los valores booleanos. Sin embargo, las comillas simples son necesarias para los valores vacíos.|  
|'`stringA`' != '`stringB`'|Se evalúa como `true` si `stringA` no es igual a `stringB`.<br /><br /> Por ejemplo:<br /><br /> `Condition="'$(CONFIG)'!='DEBUG'"`<br /><br /> Las comillas simples no son necesarias para las cadenas alfanuméricas simples o los valores booleanos. Sin embargo, las comillas simples son necesarias para los valores vacíos.|  
|\<, >, \<=, >=|Evalúa los valores numéricos de los operandos. Devuelve `true` si la evaluación relacional es verdadera. Los operandos deben evaluarse como un número decimal o hexadecimal. Los números hexadecimales deben comenzar con "0x". **Nota:** En XML, los caracteres `<` y `>` deben ser de escape. El símbolo `<` se representa como `<`. El símbolo `>` se representa como `>`.|  
|Existe ('`stringA`')|Se evalúa como `true` si existe un archivo o una carpeta con el nombre `stringA`.<br /><br /> Por ejemplo:<br /><br /> `Condition="!Exists('$(builtdir)')"`<br /><br /> Las comillas simples no son necesarias para las cadenas alfanuméricas simples o los valores booleanos. Sin embargo, las comillas simples son necesarias para los valores vacíos.|  
|HasTrailingSlash ('`stringA`')|Se evalúa como `true` si la cadena especificada contiene al final un carácter de barra inversa (\\) o barra diagonal (/).<br /><br /> Por ejemplo:<br /><br /> `Condition="!HasTrailingSlash('$(OutputPath)')"`<br /><br /> Las comillas simples no son necesarias para las cadenas alfanuméricas simples o los valores booleanos. Sin embargo, las comillas simples son necesarias para los valores vacíos.|  
|!|Se evalúa como `true` si el operando se evalúa como `false`.|  
|Y|Se evalúa como `true` si ambos operandos se evalúan como `true`.|  
|O bien|Se evalúa como `true` si al menos uno de los operandos se evalúa como `true`.|  
|()|Mecanismo de agrupamiento que se evalúa como `true` si las expresiones que contiene se evalúan como `true`.|  
|$if$ ( %expression% ), $else$, $endif$|Comprueba si el `%expression%` especificado coincide con el valor de cadena del parámetro de plantilla personalizado pasado. Si la condición `$if$` se evalúa como `true`, sus instrucciones se ejecutan; en caso contrario, se comprueba la condición `$else$`. Si la condición `$else$` es `true`, sus instrucciones se ejecutan; en caso contrario, la condición `$endif$` finaliza la evaluación de expresiones.<br /><br /> Para obtener ejemplos de uso, consulte [Lógica del parámetro Project/Item Template de Visual Studio](http://stackoverflow.com/questions/6709057/visual-studio-project-item-template-parameter-logic).|  
  
## <a name="see-also"></a>Vea también  
 [Referencia de MSBuild](../msbuild/msbuild-reference.md)   
 [Construcciones condicionales](../msbuild/msbuild-conditional-constructs.md)   
 [Tutorial: Crear un archivo del proyecto de MSBuild desde el principio](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)



