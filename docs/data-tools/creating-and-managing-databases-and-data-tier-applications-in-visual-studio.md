---
title: Los proyectos de base de datos y los proyectos DAC
ms.date: 11/21/2018
ms.topic: conceptual
helpviewer_keywords:
- databases, managing change
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d8671c46cf2e88ab5d5797dd7a009ff29b953c4e
ms.sourcegitcommit: c9a01c599ce19a5845605b3b28c0229fd0abb93f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2018
ms.locfileid: "52281737"
---
# <a name="database-projects-and-data-tier-applications"></a>Proyectos de base de datos y aplicaciones de capa de datos

Puede usar proyectos de base de datos para crear nuevas bases de datos nuevas aplicaciones de capa de datos (DAC) y para actualizar bases de datos existentes y las aplicaciones de capa de datos. Los proyectos de base de datos y los proyectos DAC permiten aplicar técnicas de administración de proyecto y control de versión a sus esfuerzos de desarrollo de base de datos de la misma manera que se aplican esas técnicas para código administrado o nativo. Puede ayudar a su equipo de desarrollo a administrar los cambios en las bases de datos y servidores de base de datos mediante la creación de un proyecto DAC, el proyecto de base de datos o un proyecto de servidor y colocarlo bajo control de versiones. Miembros del equipo, a continuación, pueden desproteger los archivos para realizar, compilar y probar los cambios en un entorno de desarrollo aislado o un espacio aislado, antes de compartirlos con el equipo. Para ayudar a garantizar la calidad del código, su equipo puede finalizar y pruebe todos los cambios para una versión concreta de la base de datos en un entorno de ensayo antes de implementar los cambios en producción.

Para obtener una lista de las características de base de datos que son compatibles con las aplicaciones de capa de datos, vea [DAC admiten objetos de SQL Server](/sql/relational-databases/data-tier-applications/dac-support-for-sql-server-objects-and-versions). Si usa características de la base de datos que no son compatibles con las aplicaciones de capa de datos, debe usar en su lugar un proyecto de base de datos para administrar los cambios en la base de datos.

## <a name="common-high-level-tasks"></a>Tareas comunes de alto nivel

| Tareas de alto nivel | Contenido adicional |
| - | - |
| **Iniciar el desarrollo de una aplicación de capa de datos:** se introdujo el concepto de una aplicación de capa de datos (DAC) con SQL Server 2008. Una DAC contiene la definición de una base de datos de SQL Server y los objetos auxiliares de instancia utilizados por una aplicación de 3 niveles o cliente-servidor. Una DAC incluye objetos de base de datos, como tablas y vistas, junto con las entidades de la instancia, como los inicios de sesión. Puede usar Visual Studio para crear un proyecto DAC, generar un archivo de paquete DAC y enviar el archivo de paquete DAC a un administrador de base de datos para la implementación en una instancia del motor de base de datos de SQL Server. | - [Aplicaciones de capa de datos](/sql/relational-databases/data-tier-applications/data-tier-applications)<br />- [SQL Server Management Studio](/sql/ssms/sql-server-management-studio-ssms) |
| **Realizar el desarrollo iterativo de la base de datos:** los desarrolladores pueden desproteger partes del proyecto y actualizarlos en un entorno de desarrollo aislado. Mediante el uso de este tipo de entorno, puede probar los cambios sin que afecte a otros miembros del equipo. Una vez completados los cambios, compruebe los archivos al control de versiones, donde otros miembros del equipo pueden obtener los cambios y generar e implementarlas en un servidor de prueba. | - [Desarrollo orientado a proyectos de base de datos sin conexión (SQL Server Data Tools)](/sql/ssdt/project-oriented-offline-database-development)<br />- [Depurador de Transact-SQL (SQL Server Management Studio)](/sql/ssms/scripting/transact-sql-debugger) |
| **Creación de prototipos, comprobación de probar los resultados y modificar los scripts de base de datos y objetos:** puede usar el editor de Transact-SQL para realizar cualquiera de estas tareas comunes. | - [Editores de consultas y texto (SQL Server Management Studio)](/sql/ssms/scripting/query-and-text-editors-sql-server-management-studio) |

## <a name="see-also"></a>Vea también

- [Visual Studio Data Tools para .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)