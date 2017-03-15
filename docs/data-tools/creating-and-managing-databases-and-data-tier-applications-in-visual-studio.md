---
title: "Creating and Managing Databases and Data-tier Applications in Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "managing change, databases"
  - "database features of Visual Studio, managing change"
  - "databases, managing change"
  - "managing change, database servers"
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
caps.latest.revision: 37
caps.handback.revision: 35
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Creating and Managing Databases and Data-tier Applications in Visual Studio
> [!IMPORTANT]
>  Los proyectos de base de datos que se incluyeron en versiones anteriores de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ahora se incluyen en las herramientas de [!INCLUDE[sql_Denali_long](../data-tools/includes/sql_denali_long_md.md)] .  Para obtener más información, vea [herramientas de desarrollo de SQL Server](http://go.microsoft.com/fwlink/?LinkId=228126).  
  
 Puede utilizar proyectos de base de datos para crear nuevas bases de datos y aplicaciones de capa de datos \(DAC\), así como para actualizar bases de datos y aplicaciones de capa de datos existentes.  Los proyectos de base de datos y los proyectos de DAC permiten aplicar técnicas de control de versiones y de administración de proyectos al desarrollo de bases de datos de manera muy similar a cómo se aplican dichas técnicas al código administrado o nativo.  Puede ayudar al equipo de desarrollo a administrar los cambios en las bases de datos y los servidores de bases de datos si crea un *proyecto de DAC*, *proyecto de base de datos* o *proyecto de servidor* y lo somete al control de versiones.  De ese modo, los miembros de un equipo podrán desproteger los archivos para realizar, compilar y probar los cambios en un *entorno de desarrollo aislado* o espacio aislado antes de compartirlos con los demás miembros del equipo.  Para asegurar la calidad del código, el equipo puede finalizar y probar todos los cambios para una versión concreta de la base de datos en un entorno de ensayo antes de implementarlos en la producción.  
  
 Para obtener una lista de las características de base de datos admitidas en aplicaciones de capa de datos, vea [Características admitidas en aplicaciones de capa de datos](http://go.microsoft.com/fwlink/?LinkId=164239) en el sitio Web de Microsoft.  Si usa características de base de datos que no se admiten en las aplicaciones de capa de datos, deberá usar un proyecto de base de datos para administrar los cambios que se realicen en la base de datos.  
  
## Tareas comunes de alto nivel  
  
|Tarea de alto nivel|Contenido adicional|  
|-------------------------|-------------------------|  
|**Iniciar el desarrollo de una aplicación de capa de datos:** una DAC es un nuevo concepto de [!INCLUDE[sskatmai_r2](../data-tools/includes/sskatmai_r2_md.md)] que contiene la definición de una base de datos de [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] y los objetos de instancia auxiliares usados por una aplicación de cliente\-servidor o una aplicación de tres niveles.  Un DAC incluye objetos de base de datos, como tablas y vistas, junto con entidades de instancia, como inicios de sesión.  Puede utilizar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para crear un proyecto de DAC, compilar un archivo de paquete de DAC y enviarlo a un administrador de bases de datos para implementarlo en una instancia del motor de base de datos de [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)].|-   [Crear y administrar aplicaciones de capa de datos](http://go.microsoft.com/fwlink/?LinkId=160741) \(sitio web de Microsoft\)<br />-   [SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=227328)|  
|**Desarrollo iterativo de bases de datos:** si es un desarrollador o evaluador, desprotege partes del proyecto y, a continuación, los actualiza en un entorno de desarrollo aislado.  Con este tipo de entorno, puede probar los cambios sin afectar a otros miembros del equipo.  Tras completar los cambios, protegerá de nuevo los archivos en el sistema de control de versiones, donde los demás miembros del equipo pueden obtener, compilar e implementar los cambios en un servidor de pruebas.|-   [consulta y editores de texto \(SQL Server Management Studio\)](http://go.microsoft.com/fwlink/?LinkId=227327) \(Sitio Web de Microsoft\)<br />-   [depurador de Transact\-SQL](http://go.microsoft.com/fwlink/?LinkId=227324) \(Sitio Web de Microsoft\)|  
|**Crear prototipos, comprobar los resultados de pruebas y modificar scripts y objetos de base de datos:** puede utilizar el editor de [!INCLUDE[tsql](../data-tools/includes/tsql_md.md)] para llevar a cabo cualquiera de estas tareas comunes.|-   [consulta y editores de texto \(SQL Server Management Studio\)](http://go.microsoft.com/fwlink/?LinkId=227327) \(Sitio Web de Microsoft\)|