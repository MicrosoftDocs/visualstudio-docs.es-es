---
title: Proyectos de base de datos y proyectos DAC
ms.date: 11/21/2018
ms.topic: conceptual
helpviewer_keywords:
- databases, managing change
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: cc8d32ddcc332264278cf76392ac69a6188ca51c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "75586736"
---
# <a name="database-projects-and-data-tier-applications"></a>Proyectos de base de datos y aplicaciones de capa de datos

Puede usar proyectos de base de datos para crear nuevas bases de datos, nuevas aplicaciones de capa de datos (DAC) y para actualizar las bases de datos y las aplicaciones de capa de datos existentes. Tanto los proyectos de base de datos como los proyectos DAC permiten aplicar técnicas de administración de proyectos y control de versiones a los esfuerzos de desarrollo de bases de datos de la misma manera que se aplican esas técnicas a código administrado o nativo. Puede ayudar a su equipo de desarrollo a administrar los cambios en las bases de datos y los servidores de bases de datos mediante la creación de un proyecto DAC, un proyecto de base de datos o un proyecto de servidor y colocarlo bajo el control de versiones. Después, los miembros del equipo pueden desproteger los archivos para realizar, compilar y probar los cambios en un entorno de desarrollo aislado, o espacio aislado, antes de compartirlos con el equipo. Para ayudar a garantizar la calidad del código, el equipo puede finalizar y probar todos los cambios de una versión determinada de la base de datos en un entorno de ensayo antes de implementar los cambios en producción.

Para obtener una lista de las características de base de datos admitidas por las aplicaciones de capa de datos, vea [compatibilidad de DAC con objetos de SQL Server](/sql/relational-databases/data-tier-applications/dac-support-for-sql-server-objects-and-versions). Si utiliza características en la base de datos que no son compatibles con las aplicaciones de capa de datos, en su lugar debe usar un proyecto de base de datos para administrar los cambios en la base de datos.

## <a name="common-high-level-tasks"></a>Tareas comunes de alto nivel

| Tarea de alto nivel | Contenido adicional |
| - | - |
| **Iniciar el desarrollo de una aplicación de capa de datos:** El concepto de una aplicación de capa de datos (DAC) se presentó con SQL Server 2008. Una DAC contiene la definición de una base de datos de SQL Server y los objetos de instancia auxiliares que usa una aplicación cliente-servidor o de tres niveles. Una DAC incluye objetos de base de datos, como tablas y vistas, junto con entidades de instancia como inicios de sesión. Puede usar Visual Studio para crear un proyecto DAC, compilar un archivo de paquete DAC y enviar el archivo de paquete DAC a un administrador de base de datos para su implementación en una instancia del motor de base de datos de SQL Server. | - [Aplicaciones de capa de datos](/sql/relational-databases/data-tier-applications/data-tier-applications)<br />- [SQL Server Management Studio](/sql/ssms/sql-server-management-studio-ssms) |
| **Desarrollo iterativo de bases de datos:** Los desarrolladores pueden desproteger partes del proyecto y actualizarlas en un entorno de desarrollo aislado. Mediante este tipo de entorno, puede probar los cambios sin que afecte a otros miembros del equipo. Una vez completados los cambios, vuelva a proteger los archivos en el control de versiones, donde otros miembros del equipo pueden obtener los cambios y compilarlos e implementarlos en un servidor de prueba. | - [Desarrollo de bases de datos sin conexión orientado a proyectos (SQL Server Data Tools)](/sql/ssdt/project-oriented-offline-database-development)<br />- [Depurador de Transact-SQL (SQL Server Management Studio)](/sql/ssms/scripting/transact-sql-debugger) |
| **Prototipos, comprobación de resultados de pruebas y modificación de objetos y scripts de base de datos:** Puede usar el editor de Transact-SQL para realizar cualquiera de estas tareas comunes. | - [Editores de consultas y texto (SQL Server Management Studio)](/sql/ssms/scripting/query-and-text-editors-sql-server-management-studio) |

## <a name="see-also"></a>Consulte también

- [Visual Studio Data Tools para .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
