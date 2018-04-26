---
title: Herramientas de Entity Framework en Visual Studio
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 0b1d98422d9527220b54232d1180ae4b91a28e6b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="entity-framework-tools-in-visual-studio"></a>Herramientas de Entity Framework en Visual Studio
Entity Framework es una tecnología de asignación objeto-relacional que permite a los desarrolladores de .NET trabajar con datos relacionales mediante el uso de objetos específicos del dominio. Elimina la necesidad de la mayor parte del código de acceso a datos que los desarrolladores normalmente deben escribir. Entity Framework es la asignación relacional de objetos (ORM) recomendada, modelado tecnología para nuevas aplicaciones de .NET.

Herramientas de Entity Framework están diseñadas para ayudarle a crear aplicaciones de Entity Framework (EF). Toda la documentación de Entity Framework está aquí: [EF núcleos y 6 de EF](/ef/).

Con herramientas de Entity Framework, puede crear un *modelo conceptual* partir de una base de datos y, a continuación, gráficamente visualizar y editar el modelo conceptual. – O bien –, primero puede crear gráficamente un modelo conceptual y, a continuación, generar una base de datos que admita su modelo. En cualquier caso, puede actualizar el modelo automáticamente cuando la base de datos subyacente cambie y generar automáticamente el código de capa de objeto para la aplicación. La generación de bases de datos y la generación del código de capa de objeto son personalizables.

Las herramientas de Entity Framework se instalan como parte de la **almacenamiento de datos y el procesamiento** carga de trabajo en el instalador de Visual Studio. También puede instalar como un componente de límites en el **SDK, bibliotecas y marcos de trabajo** categoría.

Estas son las herramientas específicas que constituyen las herramientas de Entity Framework en Visual Studio:

-   Puede usar el [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)]  **[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] diseñador** (**Entity Designer**) para crear y modificar las entidades, asociaciones, asignaciones y las relaciones de herencia visualmente. El **Entity Designer** también genera [!INCLUDE[TLA#tla_cshrp](../data-tools/includes/tlasharptla_cshrp_md.md)] o [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] código de capa de objeto.

-   Puede usar el  **[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] asistente** para generar un modelo conceptual desde una base de datos existente y agregar información de conexión de base de datos a la aplicación.

-   Puede usar el **Asistente para crear la base de datos** para crear un modelo conceptual primero y, a continuación, crear una base de datos que admita el modelo.

-   Puede usar el **Asistente para actualizar modelo** para actualizar el modelo conceptual, modelo de almacenamiento y las asignaciones cuando se han efectuado cambios en la base de datos subyacente.

    > [!NOTE]
    >  A partir de Visual Studio 2010, herramientas de Entity Framework no admiten [!INCLUDE[ss2k](../data-tools/includes/ss2k_md.md)].

Las herramientas generan o modifican un archivo .edmx. Este archivo .edmx contiene información que describe el modelo conceptual, el modelo de almacenamiento y las asignaciones entre ellos. Para obtener más información, consulte [EDMX](https://msdn.microsoft.com/data/jj650889.aspx).

[Herramientas de Entity Framework Power](https://marketplace.visualstudio.com/items?itemName=EntityFrameworkTeam.EntityFrameworkPowerToolsBeta4) le ayudará a generar las aplicaciones que utilizan el Entity Data Model. Las herramientas avanzadas pueden generar un modelo conceptual, validar un modelo existente, generar archivos de código fuente que contienen las clases de objeto basadas en el modelo conceptual y generar archivos de código fuente que contienen las vistas que genera el modelo. Para obtener información detallada, vea [vistas de asignación de Pre-Generated](https://msdn.microsoft.com/data/dn469601.aspx).

## <a name="related-topics"></a>Temas relacionados

|Título|Descripción|
|-----------|-----------------|
|[ADO.NET Entity Framework](/dotnet/framework/data/adonet/ef/index)|Describe cómo usar [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] herramientas, que [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)] proporciona para crear aplicaciones.|
|[Entity Data Model](/dotnet/framework/data/adonet/entity-data-model)|Proporciona vínculos e información para trabajar con datos que se utilizan por las aplicaciones basadas en [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)].|
|[Documentación de Entity Framework (EF))](https://msdn.microsoft.com/library/ee712907(v=vs.113).aspx)|Proporciona un índice de vídeos, tutoriales y documentación de características avanzadas que le ayudarán a sacar el máximo partido de Entity Framework.|
|[ASP.NET 5 aplicación a la nueva base de datos](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html)|Describe cómo crear una nueva aplicación ASP.NET 5 mediante Entity Framework 7.|

## <a name="see-also"></a>Vea también

- [Visual Studio Data Tools para .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)