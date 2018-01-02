---
title: "Contracción y expansión de regiones de código en Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- outlining
- Visual Studio, expand/collapse code
- Visual Studio, outlining
- expand/collapse code
- code [Visual Studio], outlining
- code [Visual Studio], hiding
- outlining code
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a3c6d848821495b5db069b4343ca5c596a064422
ms.sourcegitcommit: ebe9fb5eda724936f7a059d35d987c29dffdb50d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/07/2017
---
# <a name="outlining"></a>esquematizar

Se puede ocultar algún código de la vista si se contrae una región de código para que aparezca debajo de un signo más (+). Para expandir una región contraída hay que hacer clic en su signo más. Si prefiere usar el teclado, puede presionar **CTRL** + **M** + **M** para expandir o contraer. También se puede contraer una región de esquematización si se hace doble clic en cualquier línea de la región en el margen de esquematización, que aparece justo a la izquierda del código. Para ver el contenido de una región contraída como información sobre herramientas, hay que mantener el mouse sobre la región contraída.

Las regiones en el margen de esquematización también se resaltan cuando se mantiene el mouse sobre el margen. El color de resaltado predeterminado puede parecer bastante pálido en algunas configuraciones de color. Puede cambiarlo en **Herramientas**, **Opciones**, **Entorno**, **Fuentes y colores**, **Región contraíble**.

Al trabajar en código esquematizado, se pueden expandir las secciones en las que se desea trabajar, contraerlas cuando se haya terminado y desplazarse a otras secciones. Cuando no quiere que se muestre la esquematización, se puede usar el comando **Detener esquematización** para quitar la información de esquematización sin alterar el código subyacente.

Los comandos **Deshacer** y **Rehacer** del menú **Edición** afectan a estas acciones. **Copiar**, **Cortar**, **Pegar** y las operaciones de arrastrar y colocar conservan la información de esquematización, pero no el estado de la región contraíble. Por ejemplo, cuando copia una región que se contrae, la operación **Pegar** pegará el texto copiado como región expandida.

> [!CAUTION]
> Si se cambia una región esquematizada, se puede perder la esquematización. Por ejemplo, las eliminaciones o las operaciones Buscar y reemplazar pueden borrar el final de la región.

El submenú **Edición**, **Esquematización** puede contener los siguientes comandos.

|||
|-|-|
|Ocultar selección|(CTRL + M, CTRL + O): contrae un bloque de código seleccionado que normalmente no estaría disponible para la esquematización, por ejemplo un bloque `if`. Para quitar la región personalizada, use **Detener ocultar actual** (o CTRL + M, CTRL + U). No está disponible en Visual Basic.|  
|Alternar expansión de esquematización|: invierte el estado oculto o expandido actual de la sección de esquematización más interna cuando el cursor se encuentra en una sección contraída anidada.|  
|Alternar toda la esquematización|(CTRL + M, CTRL + L): establece todas las regiones en el mismo estado contraído o expandido. Si algunas regiones están expandidas y otras están contraídas, las regiones contraídas se expanden.|  
|Detener esquematización|(CTRL + M, CTRL + D): quita toda la información de esquematización del documento completo.|  
|Detener ocultar actual|(CTRL + M, CTRL + U): quita la información de esquematización para la región definida por el usuario que está seleccionada actualmente. No está disponible en Visual Basic.|  
|Contraer a definiciones|(CTRL + M, CTRL + N): contrae los miembros de todos los tipos.|  
|Contraer bloque:\<límite lógico>|(Visual C++) Contrae una región en la función que contiene el punto de inserción. Por ejemplo, si el punto de inserción está dentro de un bucle, se oculta el bucle.|  
|Contraer todo el contenido de: \<estructuras lógicas>|(Visual C++) Contrae todas las estructuras dentro de la función.|  

También puede utilizar Visual Studio SDK para definir las regiones de texto que desea expandir o contraer. Vea [Tutorial: esquematización](../extensibility/walkthrough-outlining.md).

## <a name="see-also"></a>Vea también

[Escribir código en el editor](../ide/writing-code-in-the-code-and-text-editor.md)