---
title: Crear y administrar bases de datos y aplicaciones de capa de datos
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- managing change, databases
- database features of Visual Studio, managing change
- databases, managing change
- managing change, database servers
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
caps.latest.revision: 40
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c2b1caf45235f9dd745841cb26a2fa10a148a7b5
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299647"
---
# <a name="creating-and-managing-databases-and-data-tier-applications-in-visual-studio"></a>Creación y administración de aplicaciones de capa de datos y bases de datos en Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

IMPORTANTE]
> Los proyectos de base de datos que se incluyeron en versiones anteriores de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ahora se proporcionan en [!INCLUDE[sql_Denali_long](../includes/sql-denali-long-md.md)] herramientas. Para obtener más información, vea [herramientas de SQL Server Developer](https://go.microsoft.com/fwlink/?LinkId=228126).

 Puede usar proyectos de base de datos para crear nuevas bases de datos, nuevas aplicaciones de capa de datos (DAC) y para actualizar las bases de datos y las aplicaciones de capa de datos existentes. Tanto los proyectos de base de datos como los proyectos DAC permiten aplicar técnicas de administración de proyectos y control de versiones a los esfuerzos de desarrollo de bases de datos de la misma manera que se aplican esas técnicas a código administrado o nativo. Puede ayudar a su equipo de desarrollo a administrar los cambios en las bases de datos y los servidores de bases de datos mediante la creación de un proyecto *DAC*, un *proyecto de base de datos*o un proyecto de *servidor* y colocarlo bajo el control de versiones. Después, los miembros del equipo pueden desproteger los archivos para realizar, compilar y probar los cambios en un *entorno de desarrollo aislado*, o espacio aislado, antes de compartirlos con el equipo. Para ayudar a garantizar la calidad del código, el equipo puede finalizar y probar todos los cambios de una versión determinada de la base de datos en un entorno de ensayo antes de implementar los cambios en producción.

 Para obtener una lista de las características de base de datos admitidas por las aplicaciones de capa de datos, vea [características compatibles con las aplicaciones de capa de datos](https://go.microsoft.com/fwlink/?LinkId=164239) en el sitio web de Microsoft. Si utiliza características en la base de datos que no son compatibles con las aplicaciones de capa de datos, en su lugar debe usar un proyecto de base de datos para administrar los cambios en la base de datos.

## <a name="common-high-level-tasks"></a>Tareas comunes de alto nivel

|Tarea de alto nivel|Contenido adicional|
|----------------------|------------------------|
|**Iniciar el desarrollo de una aplicación de capa de datos:** Una DAC es un nuevo concepto incluido en [!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)] que contiene la definición de una base de datos de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] y los objetos de instancia auxiliares que usa una aplicación cliente-servidor o de tres niveles. Una DAC incluye objetos de base de datos, como tablas y vistas, junto con entidades de instancia como inicios de sesión. Puede usar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] para crear un proyecto DAC, compilar un archivo de paquete DAC y enviar ese archivo de paquete DAC a un administrador de base de datos para su implementación en una instancia del motor de base de datos de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].|-   [crear y administrar aplicaciones de capa de datos](https://go.microsoft.com/fwlink/?LinkId=160741) (sitio web de Microsoft)<br />-   [SQL Server Management Studio](https://go.microsoft.com/fwlink/?LinkId=227328)|
|**Desarrollo iterativo de bases de datos:** Si es un desarrollador o un evaluador, revise las partes del proyecto y, a continuación, actualícelo en un entorno de desarrollo aislado. Mediante este tipo de entorno, puede probar los cambios sin que afecte a otros miembros del equipo. Una vez completados los cambios, vuelva a proteger los archivos en el control de versiones, donde otros miembros del equipo pueden obtener los cambios y compilarlos e implementarlos en un servidor de prueba.|-   [editores de consultas y texto (SQL Server Management Studio)](https://go.microsoft.com/fwlink/?LinkId=227327) (sitio web de Microsoft)<br />-   [depurador de Transact-SQL](https://go.microsoft.com/fwlink/?LinkId=227324) (sitio web de Microsoft)|
|**Prototipos, comprobación de resultados de pruebas y modificación de objetos y scripts de base de datos:** Puede usar el editor de [!INCLUDE[tsql](../includes/tsql-md.md)] para realizar cualquiera de estas tareas comunes.|-   [editores de consultas y texto (SQL Server Management Studio)](https://go.microsoft.com/fwlink/?LinkId=227327) (sitio web de Microsoft)|

## <a name="see-also"></a>Vea también
 [Visual Studio Data Tools para .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
