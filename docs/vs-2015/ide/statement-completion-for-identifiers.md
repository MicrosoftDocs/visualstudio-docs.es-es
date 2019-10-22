---
title: Finalización de instrucciones para identificadores | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense [JavaScript], statement completion
- statement completion, JavaScript IntelliSense
ms.assetid: c2cd4945-c67e-471b-8057-96cfd25f7fb2
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f5e52bf174e5a41d79fa23bfca39121db668e40e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72643853"
---
# <a name="statement-completion-for-identifiers"></a>Finalización de instrucciones para identificadores
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

JavaScript no permite tipos explícitos para las declaraciones de variables. Como resultado, IntelliSense no siempre puede proporcionar listas de finalización para objetos. Esto puede ocurrir en varias situaciones. A continuación se muestran algunos comunes.

- Se declara un parámetro, pero no se ha llamado a ningún otro lugar del documento activo, como se muestra en el ejemplo siguiente.

  ```javascript
  function illuminate(light) {
           light.  // Accurate statement completion is not available
                   // unless illuminate is called elsewhere with a
                   // parameter that has a value. If it is called only
                   // in a function that is a sibling to
                   // illuminate(light) in the call hierarchy, the
                   // IntelliSense engine also cannot determine the
                   // parameter type.
       }

  // Sibling function. No statement completion for light
  // object in preceding code.
  function lightLamp() {
      var x = illuminate(1);
  }

  // Uncomment the next line to obtain statement completion for
  // light object in preceding code.
  // var x = illuminate(1);
  ```

- Un objeto está en una función a la que se llama en respuesta a un evento. En tiempo de diseño, el motor de IntelliSense no puede determinar el tipo de objetos que se usan en esta situación.

   Si el motor de IntelliSense puede determinar que se debe llamar al evento, normalmente mediante el uso de `addEventListener` para el evento en el documento activo, se proporciona información de IntelliSense más precisa.

  Cuando IntelliSense no puede identificar un objeto, el motor de IntelliSense rellena la lista de finalización con entidades con nombre, o identificadores, que se encuentran en el documento activo. Cuando la lista de finalización contiene estos identificadores, aparecen iconos de información junto a ellos. Además, una información sobre herramientas para cada identificador indica que se desconoce la expresión. En la ilustración siguiente se muestran las opciones de finalización de instrucciones para un objeto de tipo `light` que no se puede identificar porque el objeto y sus propiedades no están definidos. Sin embargo, la propiedad `intensity` está disponible en la lista de identificadores porque se ha utilizado en la función `illuminate`.

  **Opciones de finalización de un objeto que no se puede identificar**

  ![IntelliSense para JavaScript para identificadores](../ide/media/js-intellisense-identifiers.png "|::ref1::|")

  Puede invalidar la lista de finalización de un objeto mediante comentarios de documentación XML o características de extensibilidad de IntelliSense para JavaScript. Con estas características, puede proporcionar información de tipo e información de IntelliSense más descriptiva cuando no esté disponible de otro modo. Para obtener más información, vea [extender JavaScript IntelliSense](../ide/extending-javascript-intellisense.md) y [crear comentarios de documentación XML](../ide/create-xml-documentation-comments-for-javascript-intellisense.md).

## <a name="see-also"></a>Otras referencias
 [IntelliSense para JavaScript](../ide/javascript-intellisense.md)
