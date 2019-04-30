---
title: Data tools para .NET
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
- dotnet
ms.openlocfilehash: a454218bbddb6c135ff7dc2a5910e6e4a9b3c7e4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62565091"
---
# <a name="visual-studio-data-tools-for-net"></a>Visual Studio Data Tools para .NET

Visual Studio y .NET Framework proporcionan numerosas API y herramientas de soporte técnico para conectarse a bases de datos, modelado de datos en memoria y mostrar los datos en la interfaz de usuario. Las clases de .NET Framework que proporcionan la funcionalidad de acceso a datos se conocen como [ADO.NET](/dotnet/framework/data/adonet/index). ADO.NET, junto con los datos de herramientas en Visual Studio, se diseñó principalmente para admitir bases de datos relacionales y XML. En la actualidad, muchos proveedores de base de datos NoSQL, o de terceros, ofrecen proveedores de ADO.NET.

[.NET core](/dotnet/core/) es compatible con ADO.NET, excepto para los conjuntos de datos y los tipos relacionados. Si se usa .NET Core y requieren una capa de asignación relacional de objetos (ORM), use [Entity Framework Core](/ef/core/).

El siguiente diagrama muestra una vista simplificada de la arquitectura básica:

![Arquitectura de ADO.NET](../data-tools/media/raddata-ado-net-architecture-diagram.png)

## <a name="typical-workflow"></a>Flujo de trabajo típico

El flujo de trabajo típico es el siguiente:

1. Instale un desarrollo o la base de datos de prueba en el equipo local. Consulte [instalar sistemas de base de datos, herramientas y ejemplos](../data-tools/installing-database-systems-tools-and-samples.md). Si usas un servicio de datos de Azure, este paso no es necesario.

2. Probar la conexión a la base de datos (o servicio o un archivo local) en Visual Studio. Consulte [agregar nuevas conexiones](../data-tools/add-new-connections.md).

3. (Opcional) Usar las herramientas para generar y configurar un nuevo modelo. Los modelos basados en Entity Framework son la recomendación predeterminada para las aplicaciones nuevas. El modelo, sea cual sea uno que utilice, es el origen de datos con el que interactúa la aplicación. El modelo se sitúa lógicamente entre la base de datos o servicio y la aplicación. Consulte [agregar nuevos orígenes de datos](../data-tools/add-new-data-sources.md).

4. Arrastre el origen de datos desde el **orígenes de datos** ventana hasta una superficie de diseño de Windows Forms, ASP.NET o Windows Presentation Foundation para generar el código de enlace de datos que se mostrará los datos al usuario en la forma en que especifique. Consulte [enlazar controles a datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

5. Agregar código personalizado para cosas como las reglas de negocios, búsqueda y validación de datos, así como aprovechar la funcionalidad personalizada que expone la base de datos subyacente.

Se puede omitir el paso 3 y programar una aplicación .NET para ejecutar comandos directamente a una base de datos, en lugar de utilizar un modelo. En este caso, encontrará la documentación pertinente aquí: [ADO.NET](/dotnet/framework/data/adonet/index). Tenga en cuenta que todavía puede usar el **Asistente para configuración de origen de datos** y diseñadores para generar el código de enlace de datos al rellenar sus propios objetos en memoria y, a continuación, enlazar controles de IU a esos objetos.

## <a name="see-also"></a>Vea también

- [Acceso a datos en Visual Studio](../data-tools/accessing-data-in-visual-studio.md)