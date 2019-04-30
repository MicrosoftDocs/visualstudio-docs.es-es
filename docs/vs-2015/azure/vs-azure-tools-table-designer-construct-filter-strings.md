---
title: Construcción de cadenas de filtro para el diseñador de tablas | Microsoft Docs
description: Construcción de cadenas de filtro para el Diseñador de tablas
services: visual-studio-online
author: ghogen
manager: douge
assetId: a1a10ea1-687a-4ee1-a952-6b24c2fe1a22
ms.prod: visual-studio-dev15
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
origin.date: 11/18/2016
ms.date: 09/10/2018
ms.author: v-junlch
ms.openlocfilehash: ab38ffd1f94e6c8c432d25d8408a0209e4f96e30
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62961929"
---
# <a name="constructing-filter-strings-for-the-table-designer"></a>Construcción de cadenas de filtro para el Diseñador de tablas
## <a name="overview"></a>Información general
Para filtrar los datos de una tabla de Azure que se muestra en el **Diseñador de tablas**de Visual Studio, es preciso construir una cadena de filtro y especificar en el campo de filtro. La sintaxis de la cadena de filtro la define servicios de datos de WCF y es similar a una cláusula WHERE de SQL, pero se envía a Table service a través de una solicitud HTTP. El **Diseñador de tablas** administra la codificación adecuada para el usuario, por lo que para filtrar por un valor de propiedad deseado, solo necesita escribir el nombre de la propiedad, el operador de comparación, los valores de los criterios y opcionalmente, el operador booleano en el campo de filtro. No es preciso incluir la opción de consulta $filter como lo haría si fuera a construir una dirección URL para realizar consultas en la tabla a través de la [referencia de la API REST de servicios de almacenamiento](http://go.microsoft.com/fwlink/p/?LinkId=400447).

WCF Data Services se basa en [Open Data Protocol](http://go.microsoft.com/fwlink/p/?LinkId=214805) (OData). Para obtener más información sobre la opción de consulta del sistema de filtro (**$filter**), consulte las [especificaciones de las convenciones del URI de OData](http://go.microsoft.com/fwlink/p/?LinkId=214806).

## <a name="comparison-operators"></a>Operadores de comparación
Los siguientes operadores lógicos se admiten para todos los tipos de propiedades:

| Operador lógico | DESCRIPCIÓN | Ejemplo de cadena de filtro |
| --- | --- | --- |
| eq |Igual |Ciudad eq "Redmond" |
| gt |Mayor que |Precio gt 20 |
| ge |Mayor o igual que |Precio ge 10 |
| lt |Menor que |Precio lt 20 |
| le |Menor o igual que |Precio le 100 |
| ne |No igual |Ciudad ne 'Londres' |
| y |y |Precio le 200 and Precio gt 3,5 |
| o |O bien |Precio 3,5 or Precio gt 200 |
| not |not |not isAvailable |

Al construir una cadena de filtro, las siguientes reglas son importantes:

- Use los operadores lógicos para comparar una propiedad con un valor. Tenga en cuenta que no es posible comparar una propiedad con un valor dinámico; uno de los lados de la expresión debe ser una constante.
- Todas las partes de la cadena de filtro distinguen mayúsculas de minúsculas.
- Para que el filtro devuelva resultados válidos, el valor constante debe ser del mismo tipo de datos que la propiedad. Para obtener más información sobre los tipos de propiedades que se admiten, consulte [Introducción al modelo de datos del servicio Tabla](http://go.microsoft.com/fwlink/p/?LinkId=400448).

## <a name="filtering-on-string-properties"></a>Filtro por propiedades de cadena
Al filtrar por propiedades de cadena, la constante de la cadena se escribe entre comillas simples.

En el ejemplo siguiente se filtra por las propiedades **PartitionKey** y **RowKey**; también se pueden agregar a la cadena de filtro otras propiedades que no sean de clave:

    PartitionKey eq 'Partition1' and RowKey eq '00001'

Las expresiones de filtro se pueden escribir entre paréntesis, aunque no es obligatorio:

    (PartitionKey eq 'Partition1') and (RowKey eq '00001')

Tenga en cuenta que Table service no admite consultas con caracteres comodín y que tampoco se admiten en el Diseñador de tablas. Sin embargo, puede realizar que los prefijos coincidan mediante el uso de operadores de comparación en el prefijo deseado. El ejemplo siguiente devuelve las entidades cuya propiedad LastName empieza por la letra "A":

    LastName ge 'A' and LastName lt 'B'

## <a name="filtering-on-numeric-properties"></a>Filtro por propiedades numéricas
Para filtrar por un entero o un número de punto flotante, especifique el número sin comillas.

Este ejemplo devuelve todas las entidades con una propiedad Age cuyo valor es mayor que 30:

    Age gt 30

Este ejemplo devuelve todas las entidades con una propiedad AmountDue cuyo valor es menor o igual que 100,25:

    AmountDue le 100.25

## <a name="filtering-on-boolean-properties"></a>Filtro por propiedades booleanas
Para filtrar po un valo booleano, especifique **true** o **false** sin comillas.

El ejemplo siguiente devuelve todas las entidades en las que la propiedad IsActive está establecida en **true**:

    IsActive eq true

Esta expresión de filtro también se puede escribir sin el operador lógico. En el ejemplo siguiente, Table service también devolverá todas las entidades en las que el valor de IsActive sea **true**:

    IsActive

Para devolver todas las entidades en las que el valor de IsActive sea false, puede usar el no operador:

    not IsActive

## <a name="filtering-on-datetime-properties"></a>Filtro por propiedades de fecha y hora
Para filtrar por un valor de fecha y hora, especifique la palabra clave **datetime** , seguida de la constante de fecha y hora, entre comillas simples. La constante de fecha y hora debe estar en formato UTC combinado, como se describe en [Formato de los valores de la propiedad DateTime](http://go.microsoft.com/fwlink/p/?LinkId=400449).

El siguiente ejemplo devuelve las entidades en las que la propiedad CustomerSince es igual a 10 de julio de 2008:

    CustomerSince eq datetime'2008-07-10T00:00:00Z'

<!-- Update_Description: update metedata properties -->