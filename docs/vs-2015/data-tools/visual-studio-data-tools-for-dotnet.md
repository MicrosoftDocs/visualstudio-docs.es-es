---
title: Visual Studio data tools para .NET | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 759aaa1f6860d6b8e95aeaae786532ff406acbb4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47574753"
---
# <a name="visual-studio-data-tools-for-net"></a>Visual Studio Data Tools para .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio y .NET Framework proporcionan numerosas API y herramientas de soporte técnico para conectarse a bases de datos, modelado de datos en memoria y mostrar los datos en la interfaz de usuario.  Las clases de .NET Framework que proporcionan la funcionalidad de acceso a datos se conocen como [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx). ADO.NET, junto con los datos de herramientas en Visual Studio, originalmente se diseñó principalmente para admitir bases de datos relacionales y XML. En la actualidad, muchos proveedores de base de datos NoSQL, o de terceros, ofrecen proveedores de ADO.NET.  
  
 Visual Studio 2015 Update 2 incluye las actualizaciones más recientes de [SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686\(v=vs.103\).aspx), que habilitan la compatibilidad para las características más recientes de Azure [base de datos SQL](https://azure.microsoft.com/en-us/services/sql-database/) y [SQL Server 2016](https://www.microsoft.com/en-us/server-cloud/products/sql-server-2016/). [.NET core](https://www.dotnetfoundation.org/netcore) es compatible con ADO.NET, excepto para los conjuntos de datos y los tipos relacionados. Si se usa .NET Core y requieren una capa de asignación relacional de objetos (ORM), use [Entity Framework Core](https://msdn.microsoft.com/data/ef.aspx).  
  
 El siguiente diagrama muestra una vista simplificada de la arquitectura básica:  
  
 ![Arquitectura de ADO.NET](../data-tools/media/raddata-ado-net-architecture-diagram.png "raddata diagrama de arquitectura de ADO.NET")  
  
 El flujo de trabajo típico es el siguiente:  
  
1.  Instale un desarrollo o la base de datos de prueba en el equipo local. Consulte [instalar sistemas de base de datos, herramientas y ejemplos](../data-tools/installing-database-systems-tools-and-samples.md). Si usas un servicio de datos de Azure, este paso no es necesario.  
  
2.  Probar la conexión a la base de datos (o servicio o un archivo local) en Visual Studio. Consulte [agregar nuevas conexiones](../data-tools/add-new-connections.md).  
  
3.  (Opcional) Usar las herramientas para generar y configurar un nuevo modelo. Los modelos basados en Entity Framework son la recomendación predeterminada para las aplicaciones nuevas. El modelo, sea cual sea uno que utilice, es el origen de datos que la aplicación interactúa con. El modelo se sitúa lógicamente entre la base de datos o servicio y la aplicación.  Consulte [agregar nuevos orígenes de datos](../data-tools/add-new-data-sources.md).  
  
4.  Arrastre el origen de datos desde el **orígenes de datos** ventana hasta una superficie de diseño de Windows Forms, ASP.NET o Windows Presentation Foundation para generar el código de enlace de datos que se mostrará los datos al usuario en la forma en que especifique. Consulte [enlazar controles a datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
5.  Agregar código personalizado para cosas como las reglas de negocios, búsqueda y validación de datos, así como aprovechar la funcionalidad personalizada que expone la base de datos subyacente.  
  
 Se puede omitir el paso 3 y programar una aplicación .NET para ejecutar comandos directamente a una base de datos, en lugar de utilizar un modelo. En este caso, encontrará la documentación pertinente aquí: [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx). Tenga en cuenta que todavía puede usar el Asistente para configuración de origen de datos y los diseñadores para generar el código de enlace de datos al rellenar sus propios objetos en memoria y, a continuación, enlazar controles de IU a esos objetos.  
  
## <a name="in-this-section"></a>En esta sección  
  
-   [Crear una aplicación de datos sencilla mediante ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md)  
  
-   [Agregar nuevas conexiones](../data-tools/add-new-connections.md)  
  
-   [Agregar nuevos orígenes de datos](../data-tools/add-new-data-sources.md)  
  
-   [Herramientas de Entity Data Model en Visual Studio](../data-tools/entity-data-model-tools-in-visual-studio.md)  
  
-   [Herramientas de conjunto de datos en Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)  
  
-   [Herramientas LINQ to SQL en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)  
  
-   [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)  
  
-   [Recursos adicionales para la solución de problemas de errores de acceso a datos](../data-tools/additional-resources-for-troubleshooting-data-access-errors.md)  
  
-   [Servicios de Windows Communication Foundation y Servicios de datos de WCF en Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)  
  
-   [Crear y administrar aplicaciones de capa de datos y bases de datos en Visual Studio](../data-tools/creating-and-managing-databases-and-data-tier-applications-in-visual-studio.md)  
  
-   [Recursos adicionales para la solución de problemas de errores de acceso a datos](../data-tools/additional-resources-for-troubleshooting-data-access-errors.md)  
  
## <a name="see-also"></a>Vea también  
 [Obtener acceso a los datos en Visual Studio](../data-tools/accessing-data-in-visual-studio.md)







