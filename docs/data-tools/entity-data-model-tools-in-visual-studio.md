---
title: Entity Framework Tools
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 4af96ad0f76414468fd194b7079b3c4dbdaf2a4c
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586671"
---
# <a name="entity-framework-tools-in-visual-studio"></a>Entity Framework Tools en Visual Studio

Entity Framework es una tecnología de asignación relacional de objetos que permite a los desarrolladores de .NET trabajar con datos relacionales mediante objetos específicos del dominio. Elimina la necesidad de la mayor parte del código de acceso a datos que los desarrolladores normalmente deben escribir. Entity Framework es la tecnología de modelado de asignación relacional de objetos (ORM) recomendada para las nuevas aplicaciones .NET.

Entity Framework Tools están diseñados para ayudarle a crear aplicaciones de Entity Framework (EF). La documentación completa de Entity Framework está aquí: [Overview 6](/ef/ef6/).

  > [!NOTE]
  > Los Entity Framework Tools descritos en esta página se utilizan para generar archivos *. edmx* , que no se admiten en EF Core. Para generar un modelo de EF Core a partir de una base de datos existente, vea [ingeniería inversa-EF Core](/ef/core/managing-schemas/scaffolding). Para obtener más información sobre las diferencias entre EF 6 y EF Core, consulte [Compare EF 6 y EF Core](/ef/efcore-and-ef6/).

Con Entity Framework Tools, puede crear un *modelo conceptual* a partir de una base de datos existente y, a continuación, visualizar gráficamente y editar el modelo conceptual. – O bien –, primero puede crear gráficamente un modelo conceptual y, a continuación, generar una base de datos que admita su modelo. En cualquier caso, puede actualizar el modelo automáticamente cuando la base de datos subyacente cambie y generar automáticamente el código de capa de objeto para la aplicación. La generación de bases de datos y la generación del código de capa de objeto son personalizables.

Las herramientas de Entity Framework se instalan como parte de la carga de trabajo de **procesamiento y almacenamiento de datos** en el instalador de Visual Studio. También puede instalarlos como un componente individual en la categoría **SDK, bibliotecas y marcos** .

Estas son las herramientas específicas que componen Entity Framework herramientas en Visual Studio:

- Puede usar el diseñador de [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] **[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]** (**Entity Designer**) para crear y modificar visualmente entidades, asociaciones, asignaciones y relaciones de herencia. **Entity Designer** también genera [!INCLUDE[TLA#tla_cshrp](../data-tools/includes/tlasharptla_cshrp_md.md)] o [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] código de nivel de objeto.

- Puede usar el **Asistente para[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]** para generar un modelo conceptual a partir de una base de datos existente y agregar información de conexión de base de datos a la aplicación.

- Puede usar el **Asistente para crear bases de datos** para crear un modelo conceptual primero y, a continuación, crear una base de datos que admita el modelo.

- Puede usar el **Asistente para actualizar modelo** para actualizar el modelo conceptual, el modelo de almacenamiento y las asignaciones cuando se hayan realizado cambios en la base de datos subyacente.

  > [!NOTE]
  > A partir de Visual Studio 2010, las herramientas de Entity Framework no admiten la [!INCLUDE[ss2k](../data-tools/includes/ss2k_md.md)].

Las herramientas generan o modifican un archivo *. edmx* . Este archivo *. edmx* contiene información que describe el modelo conceptual, el modelo de almacenamiento y las asignaciones entre ellos. Para obtener más información, vea [EDMX](/ef/ef6/).

[Entity Framework herramientas avanzadas](https://marketplace.visualstudio.com/items?itemName=EntityFrameworkTeam.EntityFrameworkPowerToolsBeta4) le ayudan a crear aplicaciones que usan el Entity Data Model. Las herramientas avanzadas pueden generar un modelo conceptual, validar un modelo existente, generar archivos de código fuente que contengan clases de objeto basadas en el modelo conceptual y generar archivos de código fuente que contienen las vistas que genera el modelo. Para obtener información detallada, consulte [vistas de asignación previamente generadas](https://docs.microsoft.com/ef/ef6/fundamentals/performance/pre-generated-views).

## <a name="related-topics"></a>Temas relacionados

| Title | Descripción |
| - | - |
| [ADO.NET Entity Framework](/dotnet/framework/data/adonet/ef/index) | Describe cómo usar las herramientas de [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)], que [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)] proporciona, para crear aplicaciones. |
| [Entity Data Model](/dotnet/framework/data/adonet/entity-data-model) | Proporciona vínculos e información para trabajar con datos que usan las aplicaciones basadas en [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)]. |
| [Documentación de Entity Framework (EF))](/ef/ef6/get-started) | Proporciona un índice de vídeos, tutoriales y documentación avanzada para ayudarle a sacar el máximo partido de Entity Framework. |
| [Aplicación ASP.NET 5 a nueva base de datos](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html) | Describe cómo crear una nueva aplicación de ASP.NET 5 con Entity Framework 7. |

## <a name="see-also"></a>Vea también

- [Visual Studio Data Tools para .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
