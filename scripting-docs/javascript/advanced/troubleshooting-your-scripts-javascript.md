---
title: Solución de problemas de scripts (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- automative type conversion
- troubleshooting scripts
ms.assetid: 0e0545d9-44e5-4179-befc-99a882c5c672
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d7e0193e6dc0996d5e2d0d3df7103c7705d29477
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569285"
---
# <a name="troubleshooting-your-scripts-javascript"></a>Solución de problemas de scripts (JavaScript)
Hay casos en que cualquier lenguaje de programación ofrece sorpresas. Por ejemplo, el valor `null` en [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] no se comporta igual que el valor `Null` en los lenguajes C o C++.  
  
 A continuación se indican algunas de las áreas problemáticas con que se puede encontrar al escribir scripts [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="syntax-errors"></a>Errores de sintaxis  
 Es importante prestar atención a los detalles al escribir scripts. Por ejemplo, las cadenas deben quedar incluidas entre comillas.  
  
## <a name="order-of-script-interpretation"></a>Interpretación del orden del script  
 La interpretación de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] forma parte del proceso de análisis de HTML de su explorador web. Si coloca un script dentro de la etiqueta \<HEAD> en un documento, se interpreta que está antes de cualquier parte de la etiqueta \<BODY>. Si tiene objetos creados en la etiqueta \<BODY>, no existen en el momento en que se analiza la etiqueta \<HEAD>, y el script no puede manipularlos.  
  
> [!NOTE]
>  Este comportamiento es específico de Internet Explorer. ASP y WSH tienen modelos de ejecución diferentes (al igual que otros hosts).  
  
## <a name="automatic-type-coercion"></a>Conversión de tipos automática  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] es un lenguaje débilmente tipado que incluye conversión automática. Aunque los valores con tipos distintos no son iguales, las expresiones en el ejemplo siguiente se evalúan como **true**.  
  
```JavaScript  
"100" == 100;  
false == 0;  
```  
  
 Para verificar que el tipo y el valor son los mismos, utilice el operador de igualdad estricta (===). Los siguientes casos se evalúan como false:  
  
```JavaScript  
"100" === 100;  
false === 0;  
```  
  
## <a name="operator-precedence"></a>Precedencia de operadores  
 La [precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md) determina cuándo se realiza una operación durante la evaluación de una expresión. En el ejemplo siguiente, la multiplicación se realiza antes que la resta, aunque la resta aparece en primer lugar en la expresión.  
  
```JavaScript  
theRadius = aPerimeterPoint - theCenterpoint * theCorrectionFactor;  
```  
  
## <a name="using-forin-loops-with-objects"></a>Uso de bucles for...in con objetos  
 Cuando itere a través de las propiedades de un objeto con un bucle [for...in](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md), no puede predecir ni controlar el orden en el que los campos del objeto se asignan a la variable de contador de bucle. Además, el orden puede ser distinto en implementaciones diferentes del lenguaje.  
  
## <a name="with-keyword"></a>Palabra clave with  
 La instrucción [with](../../javascript/reference/with-statement-javascript.md) resulta útil para acceder a propiedades que ya existen en un objeto especificado, pero no se puede usar para agregar propiedades a un objeto. Para crear propiedades en un objeto, debe hacer referencia al objeto concreto.  
  
## <a name="this-keyword"></a>Palabra clave this  
 Aunque use la palabra clave `this` dentro de la definición de un objeto para hacer referencia al propio objeto, no puede utilizar `this` o palabras clave similares para hacer referencia a la función que se está ejecutando cuando esa función no es una definición de objeto. Si la función debe asignarse a un objeto como un método, puede usar la palabra clave `this` dentro de la función para hacer referencia al objeto.  
  
## <a name="writing-a-script-that-writes-a-script-in-internet-explorer"></a>Escritura de un script que escribe un script en Internet Explorer  
 La etiqueta \</SCRIPT> finaliza el script actual si el intérprete la detecta. Para mostrar "\</SCRIPT>" como tal, reescriba this en dos cadenas como mínimo; por ejemplo, "\</SCR" e "IPT>", que puede concatenar, a continuación, en la instrucción que las escribe.  
  
## <a name="implicit-window-references-in-internet-explorer"></a>Referencias implícitas a una ventana de Internet Explorer  
 Ya que se puede abrir más de una ventana a la vez, cualquier referencia implícita a una ventana apunta a la ventana actual. En el caso de otras ventanas, debe usar una referencia explícita.