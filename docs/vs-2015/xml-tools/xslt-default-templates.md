---
title: Plantillas predeterminadas de XSLT | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 773dd34e-67d3-4997-8df9-b71e7f880d88
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5bb4351d6b95c7aee929274135454ecf7aa91574
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669339"
---
# <a name="xslt-default-templates"></a>Plantillas predeterminadas XSLT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se usa una plantilla predeterminada durante el procesamiento XSLT si no hay ninguna regla de plantilla explícita coincidente en la hoja de estilos. La plantilla predeterminada, también denominada regla de plantilla integrada, se define en la sección 5.8 de la recomendación W3C XSLT 1.0. La plantilla predeterminada permite que el procesador XSLT procese un nodo, aunque no haya ninguna regla de plantilla explícita que coincida. Sin embargo, como la regla de plantilla integrada no está explícitamente definida en la hoja de estilos, puede conducir a unos resultados de transformación XSLT inesperados o confusos.

 El depurador XSLT ahora muestra el código de las plantillas predeterminadas XSLT. Cuando se ejecuta paso a paso una transformación XSLT, si se usa una plantilla predeterminada, el depurador muestra la plantilla predeterminada en una ventana. Esto permite analizar el código de la plantilla predeterminada y establecer puntos de interrupción en las instrucciones.

## <a name="see-also"></a>Vea también
 [Depuración de XSLT](../xml-tools/debugging-xslt.md)
