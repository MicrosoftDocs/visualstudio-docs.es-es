---
title: Plantillas predeterminadas XSLT
description: Obtenga información sobre las plantillas predeterminadas XSLT que se usan durante el procesamiento XSLT si no hay ninguna regla de plantilla explícita coincidente en la hoja de estilos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 773dd34e-67d3-4997-8df9-b71e7f880d88
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3e8efdc1a35e6129de7e33d28fa7592ead48e17e
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350132"
---
# <a name="xslt-default-templates"></a>Plantillas predeterminadas XSLT

Se usa una plantilla predeterminada durante el procesamiento XSLT si no hay ninguna regla de plantilla explícita coincidente en la hoja de estilos. La plantilla predeterminada, también denominada regla de plantilla integrada, se define en la sección 5.8 de la recomendación W3C XSLT 1.0. La plantilla predeterminada permite que el procesador XSLT procese un nodo, aunque no haya ninguna regla de plantilla explícita que coincida. Sin embargo, como la regla de plantilla integrada no está explícitamente definida en la hoja de estilos, puede conducir a unos resultados de transformación XSLT inesperados o confusos.

El depurador XSLT ahora muestra el código de las plantillas predeterminadas XSLT. Cuando se ejecuta paso a paso una transformación XSLT, si se usa una plantilla predeterminada, el depurador muestra la plantilla predeterminada en una ventana. Esto permite analizar el código de la plantilla predeterminada y establecer puntos de interrupción en las instrucciones.

## <a name="see-also"></a>Vea también

- [Depuración de XSLT](../xml-tools/debugging-xslt.md)
