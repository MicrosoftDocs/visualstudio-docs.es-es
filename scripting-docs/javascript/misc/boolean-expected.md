---
title: Se espera un booleano | Documentos de Microsoft
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
- VS.WebClient.Help.SCRIPT5010
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 35d71b7f-53fd-44c4-a7c7-b1550c65cfd4
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cb8ec8f7244b98cfa628794b485859dbec611c19
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49868097"
---
# <a name="boolean-expected"></a>Se esperaba un tipo booleano
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