---
title: "Nodos de par&#225;metros | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: da54db0b-3a3d-48dc-858c-7ac43aa04b13
caps.latest.revision: 10
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 10
---
# Nodos de par&#225;metros
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En el Diseñador de sombras, los nodos de parámetros representan entradas para el sombreador que se encuentran en el control en cada dibujo, por ejemplo, propiedades de material, luces direccionales, posición de la cámara y tiempo.  Dado que puede cambiar estos parámetros con cada llamada a draw, puede usar el mismo sombreador para dar a un objeto diferentes aspectos.  
  
## Referencia del nodo de parámetro  
  
|Nodo|Detalles|Propiedades|  
|----------|--------------|-----------------|  
|**Posición universal de la cámara**|Posición de la cámara en el espacio global.<br /><br /> **Resultado:**<br /><br /> `Output`: `float4`<br /> Posición de la cámara.|None|  
|**dirección ligera**|Vector que define la dirección en la que se proyecta la luz desde una fuente de luz en el espacio global.<br /><br /> Se puede usar para calcular la iluminación y las contribuciones especulares en el espacio global.<br /><br /> **Resultado:**<br /><br /> `Output`: `float3`<br /> El vector desde el píxel actual a una fuente de luz.|None|  
|**material ambiente**|La contribución de color difuso del píxel actual que se atribuye a iluminación indirecta.<br /><br /> El color difuso de un píxel simula la interacción de la iluminación con superficies ásperas.  Se puede usar el parámetro de material ambiente para obtener una idea aproximada de cómo contribuye la iluminación indirecta a la apariencia de un objeto en el mundo real.<br /><br /> **Resultado:**<br /><br /> `Output`: `float4`<br /> El color difuso del píxel actual que se atribuye a iluminación indirecta \(es decir, ambiental\).|**Acceso**<br /> **Public** para permitir que la propiedad se pueda establecer desde el editor de modelos; de lo contrario, **Private**.<br /><br /> **Valor**<br /> El color difuso del píxel actual que se atribuye a iluminación indirecta \(es decir, ambiental\).|  
|**material difuso**|Color que describe cómo difumina la iluminación directa del píxel actual.<br /><br /> El color difuso de un píxel simula la interacción de la iluminación con superficies ásperas.  Puede utilizar el parámetro Color difuso de material para cambiar el modo en que el píxel actual difumina la iluminación directa: direccional, punto y luz focal.<br /><br /> **Resultado:**<br /><br /> `Output`: `float4`<br /> Color que describe cómo difumina la iluminación directa del píxel actual.|**Acceso**<br /> **Public** para permitir que la propiedad se pueda establecer desde el editor de modelos; de lo contrario, **Private**.<br /><br /> **Valor**<br /> Color que describe cómo difumina la iluminación directa del píxel actual.|  
|**material emisivo**|La contribución de color del píxel actual que se atribuye a la iluminación que se proporciona a sí mismo.<br /><br /> Puede utilizar esto para simular un objeto resplandeciente; es decir, un objeto que proporciona su propia luz.  Esta luz no afecta a otros objetos.<br /><br /> **Resultado:**<br /><br /> `Output`: `float4`<br /> Contribución de color del píxel actual que se debe a la iluminación propia proporcionada.|**Acceso**<br /> **Public** para permitir que la propiedad se pueda establecer desde el editor de modelos; de lo contrario, **Private**.<br /><br /> **Valor**<br /> Contribución de color del píxel actual que se debe a la iluminación propia proporcionada.|  
|**material especular**|Color que describe cómo refleja la iluminación directa del píxel actual.<br /><br /> El color especular de un píxel simula el modo en que interactúa la luz con las superficies lisas, tipo espejo.  Puede utilizar el parámetro Reflexión especular de material para cambiar el modo en que el píxel actual refleja la iluminación directa: direccional, punto y luz focal.<br /><br /> **Resultado:**<br /><br /> `Output`: `float4`<br /> Color que describe cómo refleja la iluminación directa del píxel actual.|**Acceso**<br /> **Public** para permitir que la propiedad se pueda establecer desde el editor de modelos; de lo contrario, **Private**.<br /><br /> **Valor**<br /> Color que describe cómo refleja la iluminación directa del píxel actual.|  
|**potencia especular material**|Valor escalar que describe la intensidad de los reflejos especulares.<br /><br /> Cuanto mayor es la potencia especular, más intensos y difíciles de conseguir son los reflejos especulares.<br /><br /> **Resultado:**<br /><br /> `Output`: `float`<br /> Término exponencial que describe la intensidad de los reflejos especulares en el material del píxel actual.|**Acceso**<br /> **Public** para permitir que la propiedad se pueda establecer desde el editor de modelos; de lo contrario, **Private**.<br /><br /> **Valor**<br /> Exponente que define la intensidad de los reflejos especulares del píxel actual.|  
|**tiempo normalizado**|El tiempo en segundos, normalizados al intervalo \[0, 1\], de modo que cuando el tiempo llega a 1, se restablece en 0.<br /><br /> Se puede usar como parámetro en los cálculos del sombreador, por ejemplo, para animar coordenadas de textura, valores de color u otros atributos.<br /><br /> **Resultado:**<br /><br /> `Output`: `float`<br /> Tiempo normalizado en segundos.|None|  
|**Time**|Tiempo en segundos.<br /><br /> Se puede usar como parámetro en los cálculos del sombreador, por ejemplo, para animar coordenadas de textura, valores de color u otros atributos.<br /><br /> **Resultado:**<br /><br /> `Output`: `float`<br /> Tiempo en segundos.|None|