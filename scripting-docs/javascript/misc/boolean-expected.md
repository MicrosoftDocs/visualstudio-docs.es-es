---
title: Se espera un booleano | Documentos de Microsoft
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5010
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 35d71b7f-53fd-44c4-a7c7-b1550c65cfd4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 82123fe2a38b3de1d6e6c015f47bc5f7edd02791
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/26/2019
ms.locfileid: "56840529"
---
# <a name="boolean-expected"></a>Se esperaba un booleano
Se intentó invocar el **Boolean.prototype.toString** o **Boolean.prototype.valueOf** método en un objeto de un tipo distinto `Boolean`. El objeto de este tipo de invocación debe ser de tipo `Boolean`. Por ejemplo:

```JavaScript
var o = new Object;
o.f = Boolean.prototype.toString;
o.f();
```

## <a name="to-correct-this-error"></a>Para corregir este error

- Solo se invoque la **Boolean.prototype.toString** o **Boolean.prototype.valueOf** métodos en objetos de tipo **booleano.**

## <a name="see-also"></a>Vea también

- [Boolean (Objeto)](../../javascript/reference/boolean-object-javascript.md)
- [Tipos de datos](../../javascript/data-types-javascript.md)
- [Control del flujo del programa](../../javascript/controlling-program-flow-javascript.md)
- [Copia, pase y comparación de datos](../../javascript/advanced/copying-passing-and-comparing-data-javascript.md)