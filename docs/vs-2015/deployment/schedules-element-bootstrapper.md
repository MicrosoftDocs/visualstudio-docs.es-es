---
title: '&lt;Las programaciones&gt; (elemento, arranque) | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Schedules> element [bootstrapper]
ms.assetid: 28d094cf-64f5-42b1-bd8a-3697082aab4f
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: c72ee64bcc174bcd11d800bbc8dd0e1b9848b746
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47577912"
---
# <a name="ltschedulesgt-element-bootstrapper"></a>&lt;Las programaciones&gt; (elemento, arranque)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [ &lt;programaciones&gt; (elemento, arranque)](https://docs.microsoft.com/visualstudio/deployment/schedules-element-bootstrapper).  
  
El `Schedules` contiene elemento `Schedule` elementos, que definen las horas específicas en los comandos definidos por el `Command` se debe ejecutar el elemento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<Schedules>  
    <Schedule  
        Name  
    >  
        <BuildList />  
        <BeforePackage />  
        <AfterPackage />  
    </Schedule>  
</Schedules>  
```  
  
## <a name="elements-and-attributes"></a>Elementos y atributos  
 El `Schedules` es un elemento secundario de la `Product` elemento. Cada `Product` elemento podría tener como máximo un `Schedules` elemento. El `Schedules` elemento no tiene atributos.  
  
## <a name="schedule"></a>Programación  
 El `Schedule` es un elemento secundario de la `Schedules` elemento. Un `Schedules` elemento debe tener al menos un `Schedule` elemento.  
  
 `Schedule` tiene el siguiente atributo.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`Name`|Requerido. El nombre del elemento de programación. Esto corresponde a la `ScheduleName` propiedad de la `Command` elemento. Cuando un `Command` hace referencia a la programación con nombre, sólo se ejecutará en el momento indicado por el que `Schedule` elemento. También se pueden asociar las programaciones del `FailIf` y `BypassIf` elementos, que restringen estas comprobaciones condicionales para la ejecución de la programación especificada. Para obtener más información, consulte [ \<comandos > elemento](../deployment/commands-element-bootstrapper.md).|  
  
 A partir de `Schedule` elemento puede tener exactamente uno de los elementos secundarios siguientes.  
  
## <a name="buildlist"></a>BuildList  
 El `BuildList` elemento indica al instalador que ejecute un comando inmediatamente después de que se inicia la aplicación de arranque.  
  
## <a name="beforepackage"></a>BeforePackage  
 El `BeforePackage` elemento indica el instalador para ejecutar un comando antes de instalar el paquete especificado.  
  
## <a name="afterpackage"></a>AfterPackage  
 El `AfterPackage` elemento indica el instalador para ejecutar un comando después de instalar el paquete especificado.  
  
## <a name="see-also"></a>Vea también  
 [\<Producto > elemento](../deployment/product-element-bootstrapper.md)   
 [Referencia de esquemas de productos y paquetes](../deployment/product-and-package-schema-reference.md)



