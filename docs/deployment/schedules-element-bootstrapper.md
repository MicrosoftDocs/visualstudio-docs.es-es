---
title: '&lt;Programaciones&gt; elemento (arranque) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Schedules> element [bootstrapper]
ms.assetid: 28d094cf-64f5-42b1-bd8a-3697082aab4f
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 2b3cba1fcb5ac2d38b08383c8906adb2037e9651
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ltschedulesgt-element-bootstrapper"></a>&lt;Programaciones&gt; elemento (arranque)
El `Schedules` contiene el elemento `Schedule` elementos, que definen las horas en que los comandos definidos por el `Command` se debe ejecutar el elemento.  
  
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
 El `Schedules` es un elemento secundario de la `Product` elemento. Cada `Product` elemento puede tener a lo sumo una `Schedules` elemento. El `Schedules` elemento no tiene atributos.  
  
## <a name="schedule"></a>Programación  
 El `Schedule` es un elemento secundario de la `Schedules` elemento. A `Schedules` elemento debe tener al menos un `Schedule` elemento.  
  
 `Schedule` tiene el siguiente atributo.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`Name`|Requerido. El nombre del elemento de programación. Esto corresponde a la `ScheduleName` propiedad de la `Command` elemento. Cuando un `Command` hace referencia a la programación con nombre, solo se ejecutará a la hora indicada por esa `Schedule` elemento. Programaciones también pueden asociar a la `FailIf` y `BypassIf` elementos, que restringen estas comprobaciones condicionales a la ejecución en la programación especificada. Para obtener más información, consulte [ \<comandos > elemento](../deployment/commands-element-bootstrapper.md).|  
  
 A partir de `Schedule` elemento puede tener exactamente uno de los elementos secundarios siguientes.  
  
## <a name="buildlist"></a>BuildList  
 El `BuildList` elemento indica al instalador que ejecute un comando inmediatamente después de que se inicia la aplicación de arranque.  
  
## <a name="beforepackage"></a>BeforePackage  
 El `BeforePackage` elemento indica al instalador que ejecute un comando antes de instalar el paquete especificado.  
  
## <a name="afterpackage"></a>AfterPackage  
 El `AfterPackage` elemento indica al instalador que ejecute un comando después de instalar el paquete especificado.  
  
## <a name="see-also"></a>Vea también  
 [\<Producto > elemento](../deployment/product-element-bootstrapper.md)   
 [Referencia de esquemas de productos y paquetes](../deployment/product-and-package-schema-reference.md)