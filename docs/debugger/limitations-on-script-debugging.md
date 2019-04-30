---
title: Limitaciones de la depuración de scripts | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- ASPX breakpoint mapping, limitations
- script debugging, limitations
- breakpoint mapping, limitations
ms.assetid: 280eead5-693c-47af-967f-dfe9d23f84db
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 69c5bb23745719edf5e67400d97202f4d14ac17d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62846265"
---
# <a name="limitations-on-script-debugging"></a>Limitaciones de la depuración de script
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] admite la depuración de script en el cliente, sujeta a las limitaciones descritas en este tema.

## <a name="limitations-on-breakpoint-mapping-with-client-side-script"></a>Limitaciones de la asignación de puntos de interrupción con script de cliente
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] permite establecer un punto de interrupción en un archivo ASPX o HTML de servidor que se transforma en un archivo de cliente en tiempo de ejecución. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] asigna el punto de interrupción del archivo de servidor a un punto de interrupción correspondiente en el archivo de cliente, sujeto a las siguientes limitaciones:

- Los puntos de interrupción se deben establecer dentro de bloques `<script>`. No se pueden asignar puntos de interrupción en script en línea o en bloques `<% %>`.

- La dirección URL del explorador de la página debe contener el nombre de página. Por ejemplo: http://microsoft.com/default.apsx. Asignación de punto de interrupción no puede reconocer una redirección desde una dirección como http://microsoft.com en la página predeterminada.

- El punto de interrupción se debe establecer en la página especificada en la dirección URL del explorador, no en un archivo de control de ASPX (ascx), la página maestra u otro archivo que incluya dicha página. No se pueden asignar puntos de interrupción establecidos en páginas incluidas.

- No se pueden asignar puntos de interrupción establecidos en bloques `<script defer=true>`.

- Para los puntos de interrupción establecidos en bloques `<script id="">`, la asignación de puntos de interrupción omite el atributo `id`.

## <a name="breakpoint-mapping-and-duplicate-lines"></a>Asignación de puntos de interrupción y líneas duplicadas
 Para buscar la ubicación correspondiente en el script de cliente y de servidor, el algoritmo de asignación de puntos de interrupción examina el código en cada línea. El algoritmo supone que cada línea es única. Si dos o más líneas contienen el mismo código, y establece un punto de interrupción en una de dichas líneas duplicadas, el algoritmo de asignación de puntos de interrupción podría seleccionar el duplicado equivocado en el archivo de cliente. Para evitarlo, agregue un comentario a la línea en la que ha establecido el punto de interrupción. Por ejemplo:

```csharp
i++ ;
i ++; // I added a comment, so this line is now unique
i ++;
```
