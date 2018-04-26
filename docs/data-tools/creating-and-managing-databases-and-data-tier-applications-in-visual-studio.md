---
title: Proyectos de base de datos, proyectos de servidor y los proyectos DAC en Visual Studio
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managing change, databases
- database features of Visual Studio, managing change
- databases, managing change
- managing change, database servers
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 84b275f2238774aacff143af17161f09006e8506
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="database-projects-and-data-tier-applications-in-visual-studio"></a>Proyectos de base de datos y aplicaciones de capa de datos en Visual Studio
Puede usar proyectos de base de datos para crear nuevas bases de datos nuevas aplicaciones de capa de datos (DAC) y para actualizar bases de datos existentes y las aplicaciones de capa de datos. Proyectos de base de datos y los proyectos DAC permiten aplicar técnicas de administración de proyecto y de control de versión para los trabajos de desarrollo de base de datos de la misma manera que se aplican dichas técnicas al código administrado o nativo. Puede ayudar a su equipo de desarrollo administrar los cambios en las bases de datos y servidores de base de datos mediante la creación de un *proyecto DAC*, *proyecto de base de datos*, o un *proyecto de servidor* y escribirlos en el control de versiones. Los miembros del equipo, a continuación, pueden desproteger los archivos para realizar, compilar y probar los cambios en un *entorno de desarrollo aislado*, o espacio aislado, antes de compartirlos con el equipo. Para ayudar a garantizar la calidad del código, el equipo puede finalizar y probar todos los cambios para una versión concreta de la base de datos en un entorno de ensayo antes de implementar los cambios en producción.

Para obtener una lista de las características de base de datos que son compatibles con las aplicaciones de capa de datos, vea [características compatibles en aplicaciones de capa de datos](http://go.microsoft.com/fwlink/?LinkId=164239) en el sitio web de Microsoft. Si usa características de la base de datos que no son compatibles con las aplicaciones de capa de datos, en su lugar, debe usar un proyecto de base de datos para administrar los cambios en la base de datos.

## <a name="common-high-level-tasks"></a>Tareas comunes de alto nivel

|Tarea de alto nivel|Contenido adicional|
|----------------------|------------------------|
|**Iniciar el desarrollo de una aplicación de capa de datos:** una DAC es un nuevo concepto que se introdujo con [!INCLUDE[sskatmai_r2](../data-tools/includes/sskatmai_r2_md.md)] que contiene la definición de un [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] objetos utilizados por un cliente / servidor o 3 niveles de instancia de base de datos y la compatibilidad con aplicación. Un DAC incluye objetos de base de datos, como tablas y vistas, junto con las entidades de instancia como inicios de sesión. Puede usar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para crear un proyecto DAC, generar un archivo empaquetado DAC y enviar ese archivo de paquete DAC a un administrador de base de datos para la implementación en una instancia de la [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] motor de base de datos.|-   [Crear y administrar aplicaciones de capa de datos](http://go.microsoft.com/fwlink/?LinkId=160741) (sitio web de Microsoft)<br />-   [SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=227328)|
|**Realizar el desarrollo iterativo de la base de datos:** si es un programador o evaluador, compruebe las partes del proyecto y, después, actualícela en un entorno de desarrollo aislado. Mediante el uso de este tipo de entorno, puede probar los cambios sin que afecte a otros miembros del equipo. Una vez completados los cambios, compruebe los archivos en el control de versiones, donde otros miembros del equipo pueden obtener los cambios y generar e implementarlas en un servidor de prueba.|-   [Editores de consultas y texto (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=227327) (sitio web de Microsoft)<br />-   [Depurador de Transact-SQL](http://go.microsoft.com/fwlink/?LinkId=227324) (sitio web de Microsoft)|
|**La creación de prototipos, comprobar resultados de pruebas y modificar scripts de base de datos y objetos:** puede utilizar el [!INCLUDE[tsql](../data-tools/includes/tsql_md.md)] editor para realizar cualquiera de estas tareas comunes.|-   [Editores de consultas y texto (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=227327) (sitio web de Microsoft)|

## <a name="see-also"></a>Vea también

- [Visual Studio Data Tools para .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
