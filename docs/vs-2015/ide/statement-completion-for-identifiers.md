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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 89f507c2f4d01cf5e3e1e983cfcb5bafd9d9a7dd
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2019
ms.locfileid: "54787657"
---
# <a name="statement-completion-for-identifiers"></a>Finalización de instrucciones para identificadores
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

JavaScript no permite explícita de tipos para las declaraciones de variable. Como resultado, IntelliSense no puede proporcionar siempre las listas de finalización para los objetos. Esto puede producirse en diversas situaciones. Estos son algunos de los más comunes.  
  
- Se declara un parámetro, pero no se llamó en otro lugar en el documento activo, como se muestra en el ejemplo siguiente.  
  
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
  
- Un objeto está en una función que se llama en respuesta a un evento. En tiempo de diseño, el motor de IntelliSense no puede determinar el tipo de los objetos utilizados en esta situación.  
  
   Si el motor de IntelliSense puede determinar que debe llamarse al evento, normalmente mediante el uso de `addEventListener` para el evento en el documento activo, se proporciona información más precisa de IntelliSense.  
  
  Cuando IntelliSense no puede identificar un objeto, el motor IntelliSense rellena la lista de finalización con entidades con nombre, o los identificadores que están presentes en el documento activo. Cuando la lista de finalización contiene estos identificadores, aparecerán iconos de información junto a ellos. Además, una información sobre herramientas para cada identificador indica que la expresión es desconocida. La siguiente ilustración muestra las opciones de finalización de un objeto de tipo de instrucción `light` que no se puede identificar porque el objeto y sus propiedades son indefinidas. Sin embargo, el `intensity` propiedad está disponible en la lista de identificador porque se ha usado en el `illuminate` función.  
  
  **Para un objeto que no se puede identificar las opciones de finalización**  
  
  ![IntelliSense para JavaScript para identificadores](../ide/media/js-intellisense-identifiers.png "js_intellisense_identifiers")  
  
  Puede reemplazar la lista de finalización de un objeto mediante el uso de comentarios de documentación XML o las características de extensibilidad de IntelliSense para JavaScript. Con estas características, puede proporcionar información de tipo y la información de IntelliSense más descriptiva cuando es posible que no estarían disponible. Para obtener más información, consulte [extender IntelliSense para JavaScript](../ide/extending-javascript-intellisense.md) y [crear comentarios de documentación XML](../ide/create-xml-documentation-comments-for-javascript-intellisense.md).  
  
## <a name="see-also"></a>Vea también  
 [IntelliSense para JavaScript](../ide/javascript-intellisense.md)
