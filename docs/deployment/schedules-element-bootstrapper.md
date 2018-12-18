---
title: '&lt;Las programaciones&gt; (elemento, arranque) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Schedules> element [bootstrapper]
ms.assetid: 28d094cf-64f5-42b1-bd8a-3697082aab4f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e891064b0f2ac522312b2bb654c4d05e9f7bf47c
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2018
ms.locfileid: "39078259"
---
# <a name="ltschedulesgt-element-bootstrapper"></a>&lt;Las programaciones&gt; (elemento, arranque)
El `Schedules` contiene elemento `Schedule` elementos, que definen las horas específicas en los comandos definidos por el `Command` se debe ejecutar el elemento.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml
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
  
## <a name="elements-and-attributes"></a>Los elementos y atributos  
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
 [Referencia de esquema de paquete y del producto](../deployment/product-and-package-schema-reference.md)