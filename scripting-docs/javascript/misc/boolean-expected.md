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
ms.openlocfilehash: b6d88815a33187e209bcba248d3c363afdd91227
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862657"
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

- [Boolean (Objeto)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean)
- [Tipo de datos](https://developer.mozilla.org/docs/Web/JavaScript/Data_structures)
- [Control del flujo del programa](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Control_flow_and_error_handling)
- [Copia, pase y comparación de datos](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Functions)