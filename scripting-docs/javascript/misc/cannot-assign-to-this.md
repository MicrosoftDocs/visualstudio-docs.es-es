---
title: No se puede asignar a 'this' | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5000
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba2b0a2b-f0f8-4698-b335-a4ab6c166671
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4a4ba5d852a7d131a88930dd66931c026074549b
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58149502"
---
# <a name="cannot-assign-to-this"></a>No se puede asignar a 'this'
Se intentó asignar un valor a **esto**. **Esto** es un [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] palabra clave que hace referencia a uno:

- el objeto que se está ejecutando actualmente un método,

- el objeto global, si no hay ningún método actual (o el método no pertenece a ningún otro objeto).

Un método es un [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] función que se invoca a través de un objeto. Dentro de un método, el **esto** palabra clave es una referencia al objeto se ha invocado el método a través de (que resulta ser el objeto creado por la llamada al constructor de clase con el **nuevo** operador).

Dentro de un método, puede usar **esto** hacer referencia al objeto actual, pero no puede asignar un nuevo valor a **esto**.

## <a name="to-correct-this-error"></a>Para corregir este error

- No intente asignar a **esto**. Para obtener acceso a una propiedad o método de un objeto con instancias, utilice el operador punto (p. ej., **circle.radius**).

  > [!NOTE]
  > No se asigne una variable creada por el usuario **esto**; es un [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] palabra reservada.

## <a name="see-also"></a>Vea también

- [this (Instrucción)](../../javascript/reference/this-statement-javascript.md)
- [Solución de problemas de los scripts](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)