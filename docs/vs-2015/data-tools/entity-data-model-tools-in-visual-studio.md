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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5f44b44cb0aa2d574d81fd63ef8541c25a4c2453
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "59002805"
---
# <a name="entity-data-model-tools-in-visual-studio"></a>Herramientas de Entity Data Model en Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


Entity Framework es una tecnología de asignación relacional de objetos que permite a los desarrolladores de .NET trabajar con datos relacionales usando objetos específicos del dominio. Elimina la necesidad de la mayor parte del código de acceso a datos que los desarrolladores normalmente deben escribir. Entity Framework es la asignación relacional de objetos (ORM) recomendada, tecnología para aplicaciones .NET de modelado.

 A partir de marzo de 2016, la versión de lanzamiento más reciente es [Entity Framework 6](https://msdn.microsoft.com/data/ef) . [Entity Framework 7](https://docs.efproject.net/en/latest/) está en versión preliminar.

 [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] Herramientas están diseñadas para ayudarle a crear [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)] aplicaciones. La documentación completa de [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] herramientas está aquí: [Entity Framework](https://msdn.microsoft.com/data/jj590134).

 Con [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] herramientas, puede crear un *modelo conceptual* partir de una máquina de base de datos y, a continuación, gráficamente visualizar y editar el modelo conceptual. – O bien –, primero puede crear gráficamente un modelo conceptual y, a continuación, generar una base de datos que admita su modelo. En cualquier caso, puede actualizar el modelo automáticamente cuando la base de datos subyacente cambie y generar automáticamente el código de capa de objeto para la aplicación. La generación de bases de datos y la generación del código de capa de objeto son personalizables.

 Estas son las herramientas específicas que componen el Entity Data Model Tools en Visual Studio 2015:

- Puede usar el [!INCLUDE[vstecado](../includes/vstecado-md.md)]  **[!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] diseñador** (**Entity Designer**) para crear y modificar las entidades, asociaciones, asignaciones y relaciones de herencia visualmente. El **Entity Designer** también genera [!INCLUDE[TLA#tla_cshrp](../includes/tlasharptla-cshrp-md.md)] o [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] código de nivel de objeto.

- Puede usar el  **[!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] asistente** para generar un modelo conceptual desde una base de datos existente y agregar información de conexión de base de datos a la aplicación.

- Puede usar el **Asistente para crear base de datos** para crear un modelo conceptual en primer lugar y, a continuación, crear una base de datos que admita el modelo.

- Puede usar el **Asistente para actualizar modelo** para actualizar el modelo conceptual, modelo de almacenamiento y las asignaciones cuando se han realizado cambios en la base de datos subyacente.

  > [!NOTE]
  >  A partir de Visual Studio 2010, [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] herramientas no admiten [!INCLUDE[ss2k](../includes/ss2k-md.md)].

  Las herramientas generan o modifican un archivo .edmx. Este archivo contiene información que describe el modelo conceptual, el modelo de almacenamiento y las asignaciones entre ellos. Para obtener más información, consulte [EDMX](https://msdn.microsoft.com/data/jj650889.aspx).

  Entity Framework Power Tools ayudan a crear aplicaciones que usan el Entity Data Model. Las herramientas pueden generar un modelo conceptual, validar un modelo existente, generar archivos de código fuente que contienen las clases de objeto basadas en el modelo conceptual y generar archivos de código fuente que contienen las vistas que genera el modelo. Para obtener información detallada, consulte [Pre-Generated asignación vistas](https://msdn.microsoft.com/data/dn469601.aspx).

## <a name="related-topics"></a>Temas relacionados

|Título|Descripción|
|-----------|-----------------|
|[ADO.NET Entity Framework](http://msdn.microsoft.com/library/a437041f-6899-4ae7-96ce-aabf528d7205)|Describe cómo usar [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] herramientas, que [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)] proporciona para crear aplicaciones.|
|[Entity Data Model](http://msdn.microsoft.com/library/2dda3d5b-4582-4ba0-a91d-fcd7a1498137)|Proporciona vínculos e información para trabajar con datos que se usan las aplicaciones basadas en [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)].|
|[Introducción a .NET completo (consola, WinForms, WPF, etcetera.)](/ef/ef6/get-started)|Proporciona tutoriales sobre cómo crear aplicaciones de escritorio de .NET que usan Entity Framework 7.|
|[ASP.NET 5 aplicación para la nueva base de datos](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html)|Describe cómo crear una nueva aplicación de ASP.NET 5 mediante el uso de Entity Framework 7.|

## <a name="see-also"></a>Vea también
 [Visual Studio Data Tools para .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
