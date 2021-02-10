---
title: '&lt;Elemento schedules &gt; (programa previo) | Microsoft Docs'
description: El elemento schedules contiene elementos Schedule, que definen las horas específicas en las que se deben ejecutar los comandos definidos por el elemento Command.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0154816985076373c3ced4981aa714971a9ded29
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949654"
---
# <a name="ltschedulesgt-element-bootstrapper"></a>&lt;Elemento schedules &gt; (programa previo)
El `Schedules` elemento contiene `Schedule` elementos, que definen las horas específicas en las que se deben ejecutar los comandos definidos por el `Command` elemento.

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
 El `Schedules` elemento es un elemento secundario del `Product` elemento. Cada `Product` elemento puede tener como máximo un `Schedules` elemento. El elemento `Schedules` no tiene atributos.

## <a name="schedule"></a>Programación
 El `Schedule` elemento es un elemento secundario del `Schedules` elemento. Un `Schedules` elemento debe tener al menos un `Schedule` elemento.

 `Schedule` tiene el siguiente atributo.

|Atributo|Descripción|
|---------------|-----------------|
|`Name`|Necesario. Nombre del elemento de programación. Esto corresponde a la `ScheduleName` propiedad del `Command` elemento. Cuando `Command` hace referencia a la programación con nombre, solo se ejecutará en el momento indicado por ese `Schedule` elemento. Las programaciones también pueden estar asociadas a los `FailIf` `BypassIf` elementos y, que restringen estas pruebas condicionales a ejecutarse en la programación especificada. Para obtener más información, consulte [Elemento \<Commands>](../deployment/commands-element-bootstrapper.md).|

 Un `Schedule` elemento determinado puede tener exactamente uno de los siguientes elementos secundarios.

## <a name="buildlist"></a>BuildList
 El `BuildList` elemento indica al instalador que ejecute un comando inmediatamente después de que se inicie la aplicación de arranque.

## <a name="beforepackage"></a>BeforePackage
 El `BeforePackage` elemento indica al instalador que ejecute un comando antes de que se instale el paquete especificado.

## <a name="afterpackage"></a>AfterPackage
 El `AfterPackage` elemento indica al instalador que ejecute un comando después de instalar el paquete especificado.

## <a name="see-also"></a>Vea también
- [Elemento \<Product>](../deployment/product-element-bootstrapper.md)
- [Referencia de esquemas de productos y paquetes](../deployment/product-and-package-schema-reference.md)