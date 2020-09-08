---
title: Herramientas de datos para .NET
ms.date: 11/04/2016
ms.topic: overview
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
- dotnet
ms.openlocfilehash: 67cf4969a5db8900910b375d4cf560b1e30da4eb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85281076"
---
# <a name="visual-studio-data-tools-for-net"></a>Visual Studio Data Tools para .NET

De forma conjunta, Visual Studio y .NET proporcionan una amplia compatibilidad con API y herramientas para conectarse a bases de datos, modelar datos en memoria y mostrar los datos en la interfaz de usuario. Las clases de .NET que proporcionan la funcionalidad de acceso a datos se conocen como [ADO.NET](/dotnet/framework/data/adonet/index). ADO.NET, junto con las herramientas de datos de Visual Studio, se ha diseñado principalmente para admitir bases de datos relacionales y XML. En la actualidad, muchos proveedores de bases de datos NoSQL, o terceros, ofrecen proveedores de ADO.NET.

[.NET Core](/dotnet/core/) admite ADO.NET, excepto para conjuntos de datos y sus tipos relacionados. Si el destino es .NET Core y se necesita una capa de asignación relacional de objetos (ORM), use [Entity Framework Core](/ef/core/).

En el diagrama siguiente se muestra una vista simplificada de la arquitectura básica:

![Arquitectura de ADO.NET](../data-tools/media/raddata-ado-net-architecture-diagram.png)

## <a name="typical-workflow"></a>Flujo de trabajo típico

El flujo de trabajo típico es el siguiente:

1. Instale una base de datos de desarrollo o de prueba en el equipo local. Vea [Instalación de sistemas de base de datos, herramientas y ejemplos](../data-tools/installing-database-systems-tools-and-samples.md). Este paso no es necesario si usa un servicio de datos de Azure.

2. Pruebe la conexión con la base de datos (o el servicio o el archivo local) en Visual Studio. Vea [Adición de nuevas conexiones](../data-tools/add-new-connections.md).

3. (Opcional) Use las herramientas para generar y configurar un nuevo modelo. Los modelos basados en Entity Framework son la recomendación predeterminada para las aplicaciones nuevas. El modelo, cualquiera que use, es el origen de datos con el que interactúa la aplicación. El modelo se sitúa lógicamente entre la base de datos o el servicio y la aplicación. Vea [Adición de nuevos orígenes de datos](../data-tools/add-new-data-sources.md).

4. Arrastre el origen de datos desde la ventana **Orígenes de datos** hasta una superficie de diseño de Windows Forms, ASP.NET o Windows Presentation Foundation para generar el código de enlace de datos que mostrará los datos al usuario de la forma que especifique. Vea [Enlace de controles a datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

5. Agregue código personalizado para elementos como reglas de negocios, búsqueda y validación de datos, o para aprovechar las ventajas de la funcionalidad personalizada que expone la base de datos subyacente.

Puede omitir el paso 3 y programar una aplicación de .NET para emitir comandos directamente a una base de datos, en lugar de usar un modelo. En este caso, encontrará la documentación pertinente aquí: [ADO.NET](/dotnet/framework/data/adonet/index). Tenga en cuenta que todavía puede usar el **Asistente para la configuración de orígenes de datos** y los diseñadores para generar código de enlace de datos al rellenar objetos propios en memoria y, después, enlazar los controles de la interfaz de usuario a esos objetos.

## <a name="see-also"></a>Consulte también

- [Acceso a datos en Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
