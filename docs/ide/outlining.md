---
title: "Esquematizaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "esquematizar"
  - "Visual Studio, expandir/contraer código"
  - "Visual Studio, esquematización"
  - "código de expandir o contraer"
  - "código [Visual Studio], esquematización"
  - "código [Visual Studio], ocultación"
  - "esquematizar código"
ms.assetid: d1476758-9d35-4d74-b63c-310661932ecd
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 34
---
# Esquematizaci&#243;n
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Se puede ocultar algún código de la vista si se contrae una región de código para que aparezca debajo de un signo más \(\+\).  Para expandir una región contraída hay que hacer clic en su signo más. \(O bien, se puede presionar CTRL \+ M \+ M para contraer una región y después CTRL\+ M \+ M para volver a expandirla\). También se puede contraer una región de esquematización si se hace doble clic en cualquier línea de la región en el margen de esquematización, que aparece justo a la izquierda del código.  Para ver el contenido de una región contraída como información sobre herramientas, hay que mantener el mouse sobre la región contraída.  
  
 Las regiones en el margen de esquematización también se resaltan cuando se mantiene el mouse sobre el margen.  El color de resaltado predeterminado puede parecer bastante pálido en algunas configuraciones de color.  Se puede cambiar en **Herramientas\/Opciones\/Entorno\/Fuentes y colores\/Región contraíble**.  
  
 Al trabajar en código esquematizado, se pueden expandir las secciones en las que se desea trabajar, contraerlas cuando se haya terminado y desplazarse a otras secciones.  Cuando no se desea que se muestre la esquematización, se puede usar el comando **Detener esquematización** para quitar la información de esquematización sin alterar el código subyacente.  
  
 Los comandos **Deshacer** y **Rehacer** del menú **Edición** afectan a estas acciones.  **Copiar**, **Cortar**, **Pegar** y las operaciones de arrastrar y colocar conservan la información de esquematización, pero no el estado de la región contraíble.  Por ejemplo, cuando copia una región que se contrae, la operación **Pegar** pegará el texto copiado como región expandida.  
  
> [!CAUTION]
>  Si se cambia una región esquematizada, se puede perder la esquematización.  Por ejemplo, las eliminaciones o las operaciones Buscar y reemplazar pueden borrar el final de la región.  
  
 El submenú **Edición\/Esquematización** puede contener los comandos siguientes.  
  
|||  
|-|-|  
|Ocultar selección|\(CTRL \+ M, CTRL \+ O\): contrae un bloque de código seleccionado que normalmente no estaría disponible para la esquematización, por ejemplo un bloque `if`.  Para quitar la región personalizada, utilice **Detener ocultar actual** \(o CTRL \+ M, CTRL \+ U\).  No está disponible en Visual Basic.|  
|Alternar expansión de esquematización|: invierte el estado oculto o expandido actual de la sección de esquematización más interna cuando el cursor se encuentra en una sección contraída anidada.|  
|Alternar toda la esquematización|\(CTRL \+ M, CTRL \+ L\): establece todas las regiones en el mismo estado contraído o expandido.  Si algunas regiones están expandidas y otras están contraídas, las regiones contraídas se expanden.|  
|Detener esquematización|\(CTRL \+ M, CTRL \+ D\): quita toda la información de esquematización del documento completo.|  
|Detener ocultar actual|\(CTRL \+ M, CTRL \+ U\): quita la información de esquematización para la región definida por el usuario que está seleccionada actualmente.  No está disponible en Visual Basic.|  
|Contraer a definiciones|\(CTRL \+ M, CTRL \+ N\): contrae los miembros de todos los tipos.|  
|Contraer bloque:\<límite lógico\>|\(Visual C\+\+\) Contrae una región en la función que contiene el punto de inserción.  Por ejemplo, si el punto de inserción está dentro de un bucle, se oculta el bucle.|  
|Contraer todo el contenido de: \<estructuras lógicas\>|\(Visual C\+\+\) Contrae todas las estructuras dentro de la función.|  
  
 También puede utilizar Visual Studio SDK para definir las regiones de texto que desea expandir o contraer.  Vea [Tutorial: esquematización](../extensibility/walkthrough-outlining.md).