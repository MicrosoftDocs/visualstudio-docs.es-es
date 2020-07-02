---
title: Se esperaba un valor booleano | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 4dbb7e55f6afe6d3edfe4e98749807732ffa05ac
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "85817676"
---
# <a name="boolean-expected"></a>Se esperaba un booleano
Intentó invocar el método **Boolean. prototype. ToString** o **Boolean. prototype. valueto** en un objeto de un tipo distinto de `Boolean` . El objeto de este tipo de invocación debe ser de tipo `Boolean` . Por ejemplo:

```JavaScript
var o = new Object;
o.f = Boolean.prototype.toString;
o.f();
```

## <a name="to-correct-this-error"></a>Para corregir este error

- Solo se invocan los métodos **Boolean. prototype. ToString** o **Boolean. prototype. valueto** en objetos de tipo **Boolean.**

## <a name="see-also"></a>Vea también

- [Boolean (Objeto)](../../javascript/reference/boolean-object-javascript.md)
- [Tipo de datos](../../javascript/data-types-javascript.md)
- [Control del flujo del programa](../../javascript/controlling-program-flow-javascript.md)
- [Copia, pase y comparación de datos](../../javascript/advanced/copying-passing-and-comparing-data-javascript.md)