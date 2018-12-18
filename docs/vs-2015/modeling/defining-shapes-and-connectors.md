---
title: Definir formas y conectores | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1fae548d-9288-4dd5-a24f-ff0d69c73628
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 61cd27b307b4761e3f7773f91583965466892285
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49812951"
---
# <a name="defining-shapes-and-connectors"></a>Definir formas y conectores
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hay varios tipos básicos de formas que puede usar para mostrar información en un diagrama en un lenguaje específico de dominio (DSL).  
  
##  <a name="shapeTypes"></a> Tipos básicos de formas y conectores  
 Un diagrama DSL muestra una colección de *formas* intervinculadas por líneas o *conectores*.  Normalmente, aunque no siempre:  
  
- Las formas son la representación visible de los elementos del modelo.  
  
- Los conectores representan relaciones de referencia.  
  
- El diagrama representa la instancia raíz del modelo.  
  
- Las relaciones de incrustación entre los elementos del modelo se muestran por contención. Por ejemplo, los elementos que representan puertos de componentes se incrustan en el componente.  
  
  Estos patrones no se aplican pero se admiten. Cuando diseñe un DSL, tenga en cuenta que el diseño de las relaciones de incrustación se verá afectado por cómo quiere presentar el modelo en la pantalla. Por el contrario, las relaciones de referencia deben reflejar los conceptos del dominio empresarial.  
  
  Hay los siguientes tipos de formas disponibles:  
  
|Tipo de forma|Descripción|  
|----------------|-----------------|  
|Forma geométrica|Forma elíptica o rectangular con fines generales. Puede mostrar elementos Decorator de texto e icono en posiciones específicas relativas a los límites de la forma.<br /><br /> Para anidar formas dentro de formas geométricas, vea [anidar formas](../modeling/nesting-shapes.md).|  
|Forma de compartimiento|Rectángulo que contiene un encabezado y compartimientos, como una clase UML. Cada compartimiento puede contener una lista de filas de texto.<br /><br /> Normalmente, las filas representan elementos incrustados debajo del elemento al que representa la forma. Para ver un ejemplo, cree un DSL con la plantilla de solución Class Diagrams (Diagramas de clases).|  
|Forma de imagen|Forma que muestra una imagen.|  
|Forma de puerto|Pequeño rectángulo diseñado para adjuntarlo al contorno de otra forma. Normalmente se usa en modelos de componentes.<br /><br /> Normalmente, el elemento de modelo al que representa un puerto se incrusta debajo del elemento al que representa la forma primaria. Para ver un ejemplo, cree un DSL con la plantilla de solución Components (Componentes).<br /><br /> De forma predeterminada, una forma de puerto puede deslizarse por los lados de su forma primaria. Puede definir una regla de límites para restringirlo a una posición determinada.<br /><br /> Puede hacer que un puerto sea muy pequeño y transparente para usarlo como punto de conexión fijo en la superficie de su forma primaria.|  
|Calles|Las calles dividen un diagrama en segmentos horizontales o verticales. La calle siempre permanece debajo de las demás formas del diagrama.<br /><br /> Normalmente, los elementos de modelo de la calle tienen elementos primarios en la raíz del modelo, y los demás elementos tienen elementos primarios en ellos. Para ver un ejemplo, cree un DSL con la plantilla de solución Task Flow (Flujo de tareas).|  
|Conectores|Normalmente, las líneas que se dibujan entre las formas representan relaciones de referencia. Puede establecer las opciones para que un conector sea recto o rectilíneo, y para que tenga diferentes tipos de punta de flecha.|  
  
##  <a name="shapeInheritance"></a> Herencia de formas  
 Una forma puede heredar de otra forma. Sin embargo, las formas deben ser del mismo tipo. Por ejemplo, de una forma geométrica solo puede heredar otra forma geométrica. Las formas heredadas tienen los compartimientos y los elementos Decorator de su forma base. Los conectores pueden heredar de otros conectores.



