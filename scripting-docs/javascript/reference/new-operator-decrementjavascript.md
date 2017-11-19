---
title: New (operador) (JavaScript) | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: new_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: new operator in JavaScript
ms.assetid: 5ea556ba-7ae6-426c-8430-9032eee5a0a5
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ad004abb534d69bed1a1bd9bbd2ae96755544b9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="new-operator-javascript"></a>new (Operador de JavaScript)
Crea un nuevo objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
new constructor ([arguments])   
```  
  
## <a name="parameters"></a>Parámetros  
 `constructor`  
 Obligatorio. El constructor del objeto. Los paréntesis pueden omitirse si el constructor no toma ningún argumento.  
  
 `arguments`  
 Opcional. Los argumentos que se pasarán al constructor del objeto nuevo.  
  
## <a name="remarks"></a>Comentarios  
 El `new` operador realiza las tareas siguientes:  
  
-   Crea un objeto sin miembros.  
  
-   Llama al constructor de ese objeto, pasando un puntero al objeto recién creado como el `this` puntero.  
  
-   El constructor inicializa, a continuación, el objeto de acuerdo con los argumentos pasados al constructor.  
  
 Estos son algunos ejemplos de usos válidos de la **nueva** operador.  
  
```JavaScript  
my_object = new Object;  
my_array = new Array();  
my_date = new Date("Jan 5 1996");  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [function (Instrucción)](../../javascript/reference/function-statement-javascript.md)