---
title: "C&#243;mo: Actualizar a LocalDB o continuar con SQL Server Express | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "LocalDB"
  - "SQL Server Express"
  - "SQL Server LocalDB"
  - "SQLEXPRESS"
  - "actualizar SQLExpress a SQLExpress"
  - "actualizar a LocalDB"
ms.assetid: 14ca6f76-f80e-4926-8020-3fee2d802b75
caps.latest.revision: 33
caps.handback.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# C&#243;mo: Actualizar a LocalDB o continuar con SQL Server Express
Este tema describe las opciones para actualizar el archivo de base de datos \(.mdf\) después de instalar [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] e incluye instrucciones para las siguientes tareas:  
  
-   Actualizar un archivo de base de datos para utilizar LocalDB  
  
-   Actualizar un archivo de base de datos para usar una versión más reciente de SQL Server Express  
  
-   El trabajo con un archivo de base de datos en [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] pero por compatibilidad con [!INCLUDE[ssKatmai_exp](../data-tools/includes/sskatmai_exp_md.md)]  
  
-   Cree SQL Server Express el motor de base de datos predeterminado  
  
 Puede utilizar [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] para abrir un proyecto que contiene un archivo de base de datos \(.mdf\) creado con una versión anterior de SQL Server Express.  Sin embargo, continuar desarrollando el proyecto en [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], debe cualquiera tener que la versión de SQL Server Express instalado en el mismo equipo que Visual Studio o, debe actualizar el archivo de base de datos para utilizar SQL Server Express LocalDB.  Si actualiza el archivo de base de datos, no podrá tener acceso a las versiones anteriores de SQL Server Express.  
  
 También puede pedir que actualizar un archivo de base de datos creado mediante [!INCLUDE[sql_Denali_exp](../data-tools/includes/sql_denali_exp_md.md)] si la versión de archivo no es compatible con la instancia de SQL Server Express que está instalada actualmente.  Para resolver el problema, Visual Studio le preguntará si desea actualizar el archivo a la versión más reciente de SQL Server Express.  
  
> [!IMPORTANT]
>  Recomendamos que haga copia el archivo de base de datos antes de que se actualice.  
  
 Antes de actualizar una base de datos, debe considerar los siguientes criterios:  
  
-   No actualice si desea trabajar en el proyecto en [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] y [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)].  
  
-   No actualice si la aplicación utiliza en los entornos que usan SQL Server Express en lugar de LocalDB.  
  
-   No actualice si la aplicación utiliza las conexiones remotas porque LocalDB no las acepta.  
  
-   No actualice si su aplicación se basa en internet information services \(IIS\).  
  
-   Considere actualizar si desea probar aplicaciones de base de datos en un entorno de espacio aislado pero no desee administrar una base de datos.  
  
### Para actualizar un archivo de base de datos para utilizar LocalDB  
  
1.  En **Explorador de servidores**, elija el botón de **Conectar con base de datos** .  
  
2.  En el cuadro de diálogo de **Agregar conexión** , especifique la información siguiente:  
  
    -   **origen de datos:** Microsoft SQL Server \(SqlClient\)  
  
    -   **nombre de Servidor:** \(\) \\ V11.0 de LocalDB  
  
    -   **adjunte un archivo de base de datos:** *Ruta de acceso*, donde es la ruta de acceso física *Ruta de acceso* del archivo principal .mdf.  
  
    -   **nombre lógico:** *Nombre*, donde es el nombre *Nombre* que desea utilizar con el archivo.  
  
3.  elija el botón de **Aceptar** .  
  
4.  Cuando se le pida, elija el botón de **Sí** para actualizar el archivo.  
  
 Se actualiza la base de datos, asociada al motor de base de datos de LocalDB, y no más en compatible con [!INCLUDE[ssKatmai_exp](../data-tools/includes/sskatmai_exp_md.md)].  
  
 También puede modificar una conexión de SQLExpress para utilizar LocalDB abriendo el menú contextual para la conexión y elige **Modificar conexión**.  En **Modificar conexión** cuadro de diálogo, cambie el nombre a \(\) \\ v11.0 de LocalDB.  En el cuadro de diálogo de **Propiedades avanzadas** , asegúrese de que **Instancia de usuario** está establecido en False.  
  
### Para actualizar a una versión más reciente de SQL Server Express  
  
1.  En el menú contextual para la conexión a la base de datos, elija **Modificar conexión**.  
  
2.  En el cuadro de diálogo de **Modificar conexión** , elija el botón de **Avanzadas** .  
  
3.  En el cuadro de diálogo de **Propiedades avanzadas** , elija el botón de **Aceptar** sin cambiar el nombre del servidor.  
  
 El archivo de base de datos se actualiza para que coincida con la versión actual de [!INCLUDE[sql_Denali_exp](../data-tools/includes/sql_denali_exp_md.md)].  
  
### Para trabajar con la base de datos en [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] pero mantener compatibilidad con [!INCLUDE[ssKatmai_exp](../data-tools/includes/sskatmai_exp_md.md)]  
  
1.  En [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], abra el proyecto sin actualizarlo.  
  
    -   Para ejecutar el proyecto, elija la tecla F5.  
  
    -   Modificar la base de datos, abra el archivo .mdf en **Explorador de soluciones**, y expanda el nodo en **Explorador de servidores** a trabajar con la base de datos como hemos hecho en [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)].  
  
### Para crear SQL Server Express el motor de base de datos predeterminado  
  
1.  En la barra de menú, elija **Herramientas**, **Opciones**.  
  
2.  En el cuadro de diálogo de **Opciones** , expanda las opciones de **Herramientas de datos** , y después elija el nodo de **Conexiones de datos** .  
  
3.  En el cuadro de texto de **Nombre de instancia de SQL Server** , especifique el nombre de la instancia de SQL Server Express que desea utilizar.  Si la instancia no se denomina, especifique `. \ SQLEXPRESS`.  
  
4.  elija el botón de **Aceptar** .  
  
 SQL Server Express será el motor de base de datos predeterminado para las aplicaciones.  
  
## Vea también  
 [Información general de datos locales](../data-tools/local-data-overview.md)   
 [Tutorial: Conectar con los datos de un archivo de base de datos local \(Windows Forms\)](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)