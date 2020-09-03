---
title: Visual Studio Data Tools para .NET | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9d591595c65f00e0198ded9492ae0b8399e363e5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670101"
---
# <a name="visual-studio-data-tools-for-net"></a>Visual Studio Data Tools para .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio y el .NET Framework juntos proporcionan una amplia compatibilidad con API y herramientas para conectarse a bases de datos, modelar datos en memoria y mostrar los datos en la interfaz de usuario.  Las clases de .NET Framework que proporcionan la funcionalidad de acceso a datos se conocen como [ADO.net](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx). ADO.NET, junto con las herramientas de datos en Visual Studio, se diseñó originalmente principalmente para admitir bases de datos relacionales y XML. Estos días, muchos proveedores de bases de datos NoSQL, o terceros, ofrecen proveedores de ADO.NET.

 Visual Studio 2015 Update 2 incluye las actualizaciones más recientes de            [SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686\(v=vs.103\).aspx), que habilitan la compatibilidad con las características más recientes de Azure [SQL Database](https://azure.microsoft.com/services/sql-database/) y [SQL Server 2016](https://www.microsoft.com/sql-server/sql-server-2016). [.Net Core](https://www.dotnetfoundation.org/projects?searchquery=dotnet+core&type=project) admite ADO.net, excepto los conjuntos de valores y los tipos relacionados. Si el destino es .NET Core y requiere una capa de asignación relacional de objetos (ORM), use [Entity Framework Core](https://msdn.microsoft.com/data/ef.aspx).

 En el diagrama siguiente se muestra una vista simplificada de la arquitectura básica:

 ![Arquitectura de ADO.NET](../data-tools/media/raddata-ado-net-architecture-diagram.png "Diagrama de arquitectura de raddata ADO.NET")

 El flujo de trabajo típico es el siguiente:

1. Instale una base de datos de desarrollo o de prueba en el equipo local. Vea [instalar sistemas de base de datos, herramientas y ejemplos](../data-tools/installing-database-systems-tools-and-samples.md). Si usa un servicio de datos de Azure, este paso no es necesario.

2. Pruebe la conexión con la base de datos (o el servicio o el archivo local) en Visual Studio. Consulte [Agregar nuevas conexiones](../data-tools/add-new-connections.md).

3. Opta Use las herramientas para generar y configurar un nuevo modelo. Los modelos basados en Entity Framework son la recomendación predeterminada para las nuevas aplicaciones. El modelo, cualquiera que use, es el origen de datos con el que interactúa la aplicación. El modelo se encuentra lógicamente entre la base de datos o el servicio y la aplicación.  Consulte [agregar nuevos orígenes de datos](../data-tools/add-new-data-sources.md).

4. Arrastre el origen de datos desde la ventana **orígenes de datos** hasta una superficie de diseño Windows Forms, ASP.NET o Windows Presentation Foundation para generar el código de enlace de datos que mostrará los datos al usuario de la forma que especifique. Vea [enlazar controles a datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

5. Agregue código personalizado para cosas como reglas de negocios, búsqueda y validación de datos, o para aprovechar las ventajas de la funcionalidad personalizada que expone la base de datos subyacente.

   Puede omitir el paso 3 y programar una aplicación .NET para emitir comandos directamente a una base de datos, en lugar de usar un modelo. En este caso, encontrará la documentación pertinente aquí: [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx). Tenga en cuenta que todavía puede usar el Asistente para la configuración de orígenes de datos y los diseñadores para generar código de enlace de datos al rellenar sus propios objetos en la memoria y, a continuación, enlazar los controles de IU de datos a esos objetos.

## <a name="in-this-section"></a>En esta sección

- [Creación de una aplicación de datos sencilla mediante ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md)

- [Agregar nuevas conexiones](../data-tools/add-new-connections.md)

- [Agregar nuevos orígenes de datos](../data-tools/add-new-data-sources.md)

- [Herramientas de Entity Data Model en Visual Studio](../data-tools/entity-data-model-tools-in-visual-studio.md)

- [Herramientas de conjunto de herramientas en Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)

- [Herramientas LINQ to SQL en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)

- [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)

- [Recursos adicionales para la solución de problemas de errores de acceso a datos](../data-tools/additional-resources-for-troubleshooting-data-access-errors.md)

- [Windows Communication Foundation servicios y WCF Data Services en Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

- [Crear y administrar aplicaciones de capa de datos y bases de datos en Visual Studio](../data-tools/creating-and-managing-databases-and-data-tier-applications-in-visual-studio.md)

- [Recursos adicionales para la solución de problemas de errores de acceso a datos](../data-tools/additional-resources-for-troubleshooting-data-access-errors.md)

## <a name="see-also"></a>Consulte también
 [Obtener acceso a datos en Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
