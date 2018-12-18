---
title: No se puede asignar a &#39;esto&#39; | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5000
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba2b0a2b-f0f8-4698-b335-a4ab6c166671
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 47e55d39e85675b37d2ac9741d1207a9e81d369e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49856657"
---
# <a name="cannot-assign-to-39this39"></a>No se puede asignar a &#39;esto&#39;
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