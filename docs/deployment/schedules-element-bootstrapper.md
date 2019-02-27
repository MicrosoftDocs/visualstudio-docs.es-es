---
title: '&lt;Las programaciones&gt; (elemento, arranque) | Microsoft Docs'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2f6e4ae90dbd36dab4f4df7f72d5ecf57ee04b1
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56639432"
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

## <a name="elements-and-attributes"></a>Elementos y atributos
 El `Schedules` es un elemento secundario de la `Product` elemento. Cada `Product` elemento podría tener como máximo un `Schedules` elemento. El elemento `Schedules` no tiene atributos.

## <a name="schedule"></a>Programación
 El `Schedule` es un elemento secundario de la `Schedules` elemento. Un `Schedules` elemento debe tener al menos un `Schedule` elemento.

 `Schedule` tiene el siguiente atributo.

|Atributo|Descripción|
|---------------|-----------------|
|`Name`|Obligatorio. El nombre del elemento de programación. Esto corresponde a la `ScheduleName` propiedad de la `Command` elemento. Cuando un `Command` hace referencia a la programación con nombre, sólo se ejecutará en el momento indicado por el que `Schedule` elemento. También se pueden asociar las programaciones del `FailIf` y `BypassIf` elementos, que restringen estas comprobaciones condicionales para la ejecución de la programación especificada. Para obtener más información, consulte [ \<comandos > elemento](../deployment/commands-element-bootstrapper.md).|

 A partir de `Schedule` elemento puede tener exactamente uno de los elementos secundarios siguientes.

## <a name="buildlist"></a>BuildList
 El `BuildList` elemento indica al instalador que ejecute un comando inmediatamente después de que se inicia la aplicación de arranque.

## <a name="beforepackage"></a>BeforePackage
 El `BeforePackage` elemento indica el instalador para ejecutar un comando antes de instalar el paquete especificado.

## <a name="afterpackage"></a>AfterPackage
 El `AfterPackage` elemento indica el instalador para ejecutar un comando después de instalar el paquete especificado.

## <a name="see-also"></a>Vea también
- [\<Producto > elemento](../deployment/product-element-bootstrapper.md)
- [Referencia de esquemas de productos y paquetes](../deployment/product-and-package-schema-reference.md)