---
title: Herramientas de Entity Data Model
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d663b86603145f8a665f189e5abfbfa2b0b360ae
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672392"
---
# <a name="entity-data-model-tools-in-visual-studio"></a>Herramientas de Entity Data Model en Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Entity Framework es una tecnología de asignación relacional de objetos que permite a los desarrolladores de .NET trabajar con datos relacionales mediante objetos específicos del dominio. Elimina la necesidad de usar la mayoría del código de acceso a datos que los programadores suelen tener que escribir. Entity Framework es la tecnología de modelado de asignación relacional de objetos (ORM) recomendada para las nuevas aplicaciones .NET.

 A partir del 2016 de marzo, la versión de lanzamiento más reciente es [Entity Framework 6](https://msdn.microsoft.com/data/ef) . [Entity Framework 7](https://docs.efproject.net/en/latest/) está en versión preliminar.

 [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] Las herramientas de están diseñadas para ayudarle a crear [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)] aplicaciones de. La documentación completa de [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] las herramientas está aquí: [Entity Framework](https://msdn.microsoft.com/data/jj590134).

 Con [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] las herramientas de, puede crear un *modelo conceptual* a partir de una base de datos existente y, a continuación, visualizar y modificar gráficamente el modelo conceptual. – O bien –, primero puede crear gráficamente un modelo conceptual y, a continuación, generar una base de datos que admita su modelo. En cualquier caso, puede actualizar el modelo automáticamente cuando la base de datos subyacente cambie y generar automáticamente el código de capa de objeto para la aplicación. La generación de bases de datos y la generación del código de capa de objeto son personalizables.

 Estas son las herramientas específicas que componen Entity Data Model herramientas en Visual Studio 2015:

- Puede usar el [!INCLUDE[vstecado](../includes/vstecado-md.md)] ** [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] Diseñador** (**Entity Designer**) para crear y modificar visualmente entidades, asociaciones, asignaciones y relaciones de herencia. **Entity Designer** también genera [!INCLUDE[TLA#tla_cshrp](../includes/tlasharptla-cshrp-md.md)] código de [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] nivel de objeto o.

- Puede usar el ** [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] Asistente** para generar un modelo conceptual a partir de una base de datos existente y agregar información de conexión de base de datos a la aplicación.

- Puede usar el **Asistente para crear bases de datos** para crear un modelo conceptual primero y, a continuación, crear una base de datos que admita el modelo.

- Puede usar el **Asistente para actualizar modelo** para actualizar el modelo conceptual, el modelo de almacenamiento y las asignaciones cuando se hayan realizado cambios en la base de datos subyacente.

  > [!NOTE]
  > A partir de Visual Studio 2010, [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] las herramientas no admiten [!INCLUDE[ss2k](../includes/ss2k-md.md)] .

  Las herramientas generan o modifican un archivo. edmx. Este archivo contiene información que describe el modelo conceptual, el modelo de almacenamiento y las asignaciones entre ellos. Para obtener más información, vea  [EDMX](https://msdn.microsoft.com/data/jj650889.aspx).

  Entity Framework herramientas avanzadas le ayudan a crear aplicaciones que usan el Entity Data Model. Las herramientas de pueden generar un modelo conceptual, validar un modelo existente, generar archivos de código fuente que contengan clases de objeto basadas en el modelo conceptual y generar archivos de código fuente que contengan vistas que genera el modelo. Para obtener información detallada, consulte [vistas de asignación previamente generadas](https://msdn.microsoft.com/data/dn469601.aspx).

## <a name="related-topics"></a>Temas relacionados

|Title|Descripción|
|-----------|-----------------|
|[ADO.NET Entity Framework](https://msdn.microsoft.com/library/a437041f-6899-4ae7-96ce-aabf528d7205)|Describe cómo usar [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] las herramientas de, que [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)] proporciona, para crear aplicaciones de.|
|[Entity Data Model](https://msdn.microsoft.com/library/2dda3d5b-4582-4ba0-a91d-fcd7a1498137)|Proporciona vínculos e información para trabajar con datos que usan las aplicaciones de creadas en [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)] .|
|[Introducción en .NET completo (consola, WinForms, WPF, etc.)](/ef/ef6/get-started)|Proporciona tutoriales sobre cómo crear aplicaciones de escritorio de .NET que usan Entity Framework 7.|
|[Aplicación ASP.NET 5 a nueva base de datos](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html)|Describe cómo crear una nueva aplicación de ASP.NET 5 con Entity Framework 7.|

## <a name="see-also"></a>Consulte también
 [Visual Studio Data Tools para .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
