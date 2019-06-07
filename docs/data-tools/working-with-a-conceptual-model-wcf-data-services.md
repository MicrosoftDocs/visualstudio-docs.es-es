---
title: Trabajar con un modelo conceptual (Servicios de datos de WCF)
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], querying a service
- data [Visual Studio], LINQ to Entities
- data [Visual Studio], querying an EDM
ms.assetid: 2cd873cf-b010-49f2-a278-bb1277aaa934
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 7e92885e652c9456503bfa75fbce5640c377b684
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/06/2019
ms.locfileid: "66745346"
---
# <a name="work-with-a-conceptual-model-wcf-data-services"></a>Trabajar con un modelo Conceptual (WCF Data Services)

Cuando se usa un modelo conceptual para describir los datos de una base de datos, se pueden consultar los datos a través de objetos en lugar de tener que traducirlos en ambos sentidos entre un esquema de base de datos y un modelo de objetos.

 Puede usar los modelos conceptuales con aplicaciones de Data Services de WCF. En los temas siguientes se muestra cómo consultar los datos a través de un modelo conceptual.

| Tema | Descripción |
| - | - |
| [Cómo: Ejecutar consultas de servicios de datos](/dotnet/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services) | Muestra cómo consultar un servicio de datos desde una aplicación. NET. |
| [Cómo: Resultados de la consulta](/dotnet/framework/data/wcf/how-to-project-query-results-wcf-data-services) | Muestra cómo reducir la cantidad de datos devueltos con una consulta de servicio de datos. |

 Cuando se usa un modelo conceptual, puede definir los tipos de datos válidos en el lenguaje que coincide con su dominio. Puede definir los datos válidos en el modelo, o puede agregar validación a las operaciones que se realizan en una entidad o un servicio de datos.

 En los temas siguientes se muestra cómo agregar validación a las aplicaciones de Data Services de WCF.

|Tema|Descripción|
|-----------|-----------------|
|[Cómo: Interceptar mensajes de servicio de datos](/dotnet/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services)|Muestra cómo agregar validación a una operación de servicio de datos.|

 En los temas siguientes se muestra cómo crear, actualizar y eliminar datos mediante operaciones que se ejecutan en las entidades.

|Tema|Descripción|
|-----------|-----------------|
|[Cómo: Agregar, modificar y eliminar entidades](/dotnet/framework/data/wcf/how-to-add-modify-and-delete-entities-wcf-data-services)|Muestra cómo crear, actualizar y eliminar los datos de entidad en un servicio de datos.|
|[Cómo: Definir relaciones de entidades](/dotnet/framework/data/wcf/how-to-define-entity-relationships-wcf-data-services)|Muestra cómo crear o cambiar las relaciones en un servicio de datos.|

## <a name="see-also"></a>Vea también

- [Servicios de Windows Communication Foundation y Servicios de datos de WCF en Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
- [Consultar el servicio de datos](/dotnet/framework/data/wcf/querying-the-data-service-wcf-data-services)