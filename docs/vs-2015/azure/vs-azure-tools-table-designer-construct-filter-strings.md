---
title: Construcción de cadenas de filtro para el Diseñador de tablas | Microsoft Docs
description: Construcción de cadenas de filtro para el Diseñador de tablas
author: ghogen
manager: douge
assetId: a1a10ea1-687a-4ee1-a952-6b24c2fe1a22
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/18/2016
ms.author: ghogen
ms.openlocfilehash: ff8c3dd927e81b9e131242a9a6631a8297046a6e
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002875"
---
# <a name="constructing-filter-strings-for-the-table-designer"></a>Construcción de cadenas de filtro para el Diseñador de tablas
## <a name="overview"></a>Información general
Para filtrar los datos en una tabla de Azure que se muestra en Visual Studio **Diseñador de tablas**, construir una cadena de filtro y escríbalo en el campo de filtro. La sintaxis de la cadena de filtro se define mediante WCF Data Services y es similar a una cláusula WHERE de SQL, pero se envía a Table service a través de una solicitud HTTP. El **Diseñador de tablas** administra la codificación adecuada para usted, por lo que para filtrar según un valor de propiedad deseada, sólo necesita escribir el valor booleano nombre de propiedad, operador de comparación, valores de los criterios y si lo desea, operador en el campo de filtro. No es necesario incluir la opción de consulta $filter como lo haría si estuviese creando una dirección URL para consultar la tabla a través de la [referencia de API de REST de servicios de almacenamiento](http://go.microsoft.com/fwlink/p/?LinkId=400447).

WCF Data Services se basan en el [Open Data Protocol](http://go.microsoft.com/fwlink/p/?LinkId=214805) (OData). Para obtener más información sobre la opción de consulta de filtro del sistema (**$filter**), consulte el [especificación OData URI Conventions](http://go.microsoft.com/fwlink/p/?LinkId=214806).

## <a name="comparison-operators"></a>Operadores de comparación
Se admiten los siguientes operadores lógicos para todos los tipos de propiedad:

| Operador lógico | Descripción | Ejemplo de cadena de filtro |
| --- | --- | --- |
| eq |Igual |Ciudad eq "Redmond" |
| gt |Mayor que |Precio gt 20 |
| GE |Mayor o igual que |Precio ge 10 |
| lt |Menor que |Precio lt 20 |
| le |Menor o igual que |Precio le 100 |
| ne |No igual |Ciudad ne 'Londres' |
| y |Y |Precio le 200 and precio gt 3,5 |
| o |O bien |Precio 3,5 or precio gt 200 |
| not |no |no isAvailable |

Al construir una cadena de filtro, son importantes las siguientes reglas:

* Utilice los operadores lógicos para comparar una propiedad con un valor. Tenga en cuenta que no es posible comparar una propiedad con un valor dinámico; una parte de la expresión debe ser una constante.
* Todas las partes de la cadena de filtro distinguen mayúsculas de minúsculas.
* El valor constante debe ser del mismo tipo de datos como la propiedad en orden para el filtro devuelva resultados válidos. Para obtener más información acerca de los tipos de propiedad admitidos, consulte [Introducción al modelo de datos del servicio tabla](http://go.microsoft.com/fwlink/p/?LinkId=400448).

## <a name="filtering-on-string-properties"></a>Filtrar según propiedades de cadena
Cuando se filtra según las propiedades de cadena, encierre la constante de cadena entre comillas simples.

En el ejemplo siguiente se filtra según la **PartitionKey** y **RowKey** propiedades; adicional que no son clave también se pueden agregar propiedades a la cadena de filtro:

    PartitionKey eq 'Partition1' and RowKey eq '00001'

Cada expresión de filtro puede incluir entre paréntesis, aunque no es necesario:

    (PartitionKey eq 'Partition1') and (RowKey eq '00001')

Tenga en cuenta que Table service no admite consultas con caracteres comodín y no se admiten en el Diseñador de tablas o bien. Sin embargo, puede realizar los prefijos coincidan mediante el uso de operadores de comparación en el prefijo deseado. El ejemplo siguiente devuelve las entidades cuya propiedad LastName empieza con la letra "A":

    LastName ge 'A' and LastName lt 'B'

## <a name="filtering-on-numeric-properties"></a>Filtro por propiedades numéricas
Para filtrar por un entero o número de punto flotante, especifique el número sin comillas.

En este ejemplo devuelve todas las entidades con una propiedad Age cuyo valor es mayor que 30:

    Age gt 30

En este ejemplo devuelve todas las entidades con una propiedad AmountDue cuyo valor es menor o igual que 100,25:

    AmountDue le 100.25

## <a name="filtering-on-boolean-properties"></a>Filtro por propiedades booleanas
Para filtrar según un valor booleano, especifique **true** o **false** sin comillas.

El ejemplo siguiente devuelve todas las entidades donde se establece la propiedad IsActive en **true**:

    IsActive eq true

También puede escribir esta expresión de filtro sin el operador lógico. En el ejemplo siguiente, Table service también devolverá todas las entidades donde IsActive sea **true**:

    IsActive

Para devolver todas las entidades donde IsActive sea false, puede usar el no operador:

    not IsActive

## <a name="filtering-on-datetime-properties"></a>Filtrar según propiedades de fecha y hora
Para filtrar según un valor de fecha y hora, especifique el **datetime** palabra clave, seguida de la constante de fecha y hora entre comillas simples. La constante de fecha y hora debe estar en formato UTC combinado, tal como se describe en [dar formato a valores de propiedad de fecha y hora](http://go.microsoft.com/fwlink/p/?LinkId=400449).

El ejemplo siguiente devuelve las entidades donde la propiedad CustomerSince es igual a 10 de julio de 2008:

    CustomerSince eq datetime'2008-07-10T00:00:00Z'
