---
title: Creación y administración de bases de datos y aplicaciones de capa de datos
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4c3a8a1f4b0c6e242e3999d870fdfcdc764d8336
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58988951"
---
# <a name="creating-and-managing-databases-and-data-tier-applications-in-visual-studio"></a>Creación y administración de bases de datos y aplicaciones de capa de datos en Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


IMPORTANTE]
>  Los proyectos de base de datos que se incluyeron en versiones anteriores de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ahora se ofrecen en [!INCLUDE[sql_Denali_long](../includes/sql-denali-long-md.md)] herramientas. Para obtener más información, consulte [SQL Server Developer Tools](http://go.microsoft.com/fwlink/?LinkId=228126).

 Puede usar proyectos de base de datos para crear nuevas bases de datos nuevas aplicaciones de capa de datos (DAC) y para actualizar bases de datos existentes y las aplicaciones de capa de datos. Los proyectos de base de datos y los proyectos DAC permiten aplicar técnicas de administración de proyecto y control de versión a sus esfuerzos de desarrollo de base de datos de la misma manera que se aplican esas técnicas para código administrado o nativo. Puede ayudar a su equipo de desarrollo de administrar los cambios en las bases de datos y servidores de base de datos mediante la creación de un *proyecto DAC*, *proyecto de base de datos*, o un *proyecto de servidor* y colocarla bajo control de versiones. Miembros del equipo, a continuación, pueden desproteger los archivos para realizar, compilar y probar los cambios en un *entorno de desarrollo aislado*, o espacio aislado, antes de compartirlos con el equipo. Para ayudar a garantizar la calidad del código, su equipo puede finalizar y pruebe todos los cambios para una versión concreta de la base de datos en un entorno de ensayo antes de implementar los cambios en producción.

 Para obtener una lista de las características de base de datos que son compatibles con las aplicaciones de capa de datos, vea [características compatibles con las aplicaciones de capa de datos](http://go.microsoft.com/fwlink/?LinkId=164239) en el sitio web de Microsoft. Si usa características de la base de datos que no son compatibles con las aplicaciones de capa de datos, debe usar en su lugar un proyecto de base de datos para administrar los cambios en la base de datos.

## <a name="common-high-level-tasks"></a>Tareas comunes de alto nivel

|Tareas de alto nivel|Contenido adicional|
|----------------------|------------------------|
|**Iniciar el desarrollo de una aplicación de capa de datos:** Una DAC es un concepto nuevo introducido con [!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)] que contiene la definición de un [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] objetos utilizados por un cliente / servidor o una aplicación de 3 niveles de instancia de base de datos y el correspondiente. Una DAC incluye objetos de base de datos, como tablas y vistas, junto con las entidades de la instancia, como los inicios de sesión. Puede usar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] para crear un proyecto DAC, generar un archivo empaquetado DAC y enviar ese archivo de paquete DAC a un administrador de base de datos para la implementación en una instancia de la [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] motor de base de datos.|-   [Creación y administración de aplicaciones de capa de datos](http://go.microsoft.com/fwlink/?LinkId=160741) (sitio web de Microsoft)<br />-   [SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=227328)|
|**Realizar el desarrollo iterativo de la base de datos:** Si es un desarrollador o evaluador, comprueba las partes del proyecto y, a continuación, actualizarlos en un entorno de desarrollo aislado. Mediante el uso de este tipo de entorno, puede probar los cambios sin que afecte a otros miembros del equipo. Una vez completados los cambios, compruebe los archivos al control de versiones, donde otros miembros del equipo pueden obtener los cambios y generar e implementarlas en un servidor de prueba.|-   [Editores de consultas y texto (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=227327) (sitio web de Microsoft)<br />-   [Depurador de Transact-SQL](http://go.microsoft.com/fwlink/?LinkId=227324) (sitio web de Microsoft)|
|**Creación de prototipos, comprobar resultados de pruebas y modificar los scripts de base de datos y objetos:** Puede usar el [!INCLUDE[tsql](../includes/tsql-md.md)] editor para realizar cualquiera de estas tareas comunes.|-   [Editores de consultas y texto (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=227327) (sitio web de Microsoft)|

## <a name="see-also"></a>Vea también
 [Visual Studio Data Tools para .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
