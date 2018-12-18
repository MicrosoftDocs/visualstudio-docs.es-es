---
title: Plantillas predeterminadas XSLT | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 773dd34e-67d3-4997-8df9-b71e7f880d88
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4a26349a60c40552d350f156bf1109544a03d411
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49181355"
---
# <a name="xslt-default-templates"></a>Plantillas predeterminadas XSLT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se usa una plantilla predeterminada durante el procesamiento XSLT si no hay ninguna regla de plantilla explícita coincidente en la hoja de estilos. La plantilla predeterminada, también denominada regla de plantilla integrada, se define en la sección 5.8 de la recomendación W3C XSLT 1.0. La plantilla predeterminada permite que el procesador XSLT procese un nodo, aunque no haya ninguna regla de plantilla explícita que coincida. Sin embargo, como la regla de plantilla integrada no está explícitamente definida en la hoja de estilos, puede conducir a unos resultados de transformación XSLT inesperados o confusos.  
  
 El depurador XSLT ahora muestra el código de las plantillas predeterminadas XSLT. Cuando se ejecuta paso a paso una transformación XSLT, si se usa una plantilla predeterminada, el depurador muestra la plantilla predeterminada en una ventana. Esto permite analizar el código de la plantilla predeterminada y establecer puntos de interrupción en las instrucciones.  
  
## <a name="see-also"></a>Vea también  
 [Depuración de XSLT](../xml-tools/debugging-xslt.md)

