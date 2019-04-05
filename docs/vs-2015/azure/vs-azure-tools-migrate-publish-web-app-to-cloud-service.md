---
title: Procedimiento para migrar y publicar una aplicación web en un servicio en la nube de Azure
description: Procedimiento para migrar y publicar una aplicación web en un servicio en la nube de Azure desde Visual Studio
author: ghogen
manager: jillfra
ms.assetid: 9394adfd-a645-4664-9354-dd5df08e8c91
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/10/2017
ms.author: ghogen
ms.openlocfilehash: 2bd574fe6a3a75a46d827f459bbbdf0f3c4f807e
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "59002532"
---
# <a name="how-to-migrate-and-publish-a-web-application-to-an-azure-cloud-service-from-visual-studio"></a>Procedimiento Migración y publicación de una aplicación web a un servicio en la nube de Azure desde Visual Studio

Para aprovechar los servicios de hospedaje y la escalabilidad de Azure, puede migrar e implementar la aplicación web en un servicio en la nube de Azure. Solo se requieren cambios mínimos. En este artículo se trata solo cómo implementar solo en Cloud Services; para App Service, vea [Implementación de una aplicación web en Azure App Service](/azure/app-service/app-service-deploy-local-git).

> [!Important]
> Esta migración solo se admite para proyectos específicos de ASP.NET, Silverlight, WCF y WCF Workflow. No se admite para los proyectos de ASP.NET Core. Vea [Plantillas de proyecto compatibles](#supported-project-templates).

## <a name="migrate-a-project-to-cloud-services"></a>Migración de un proyecto a Cloud Services

1. Haga clic con el botón derecho en el proyecto de aplicación web y seleccione **Convertir > Convertir en un proyecto de servicio en la nube de Microsoft Azure**. (Tenga en cuenta que este comando no aparece si ya tiene un proyecto de rol web en la solución).
1. Visual Studio crea un proyecto de servicio en la nube en la solución que contiene el rol web necesario. El nombre de este proyecto es el mismo que el proyecto de aplicación más el sufijo `.Azure`.
1. Visual Studio también establece la propiedad **Copia local**en true para todos los ensamblados necesarios para MVC 2, MVC 3, MVC 4 y las aplicaciones empresariales de Silverlight. Esta propiedad agrega estos ensamblados al paquete de servicio empleado para la implementación.

   > [!Important]
   > Si tiene otros ensamblados o archivos que son necesarios para esta aplicación web, debe establecer manualmente las propiedades para estos archivos. Para obtener más información sobre cómo establecer estas propiedades, vea [Incluir archivos en el paquete de servicio](vs-azure-tools-publishing-a-cloud-service.md#include-files-in-the-service-package).

### <a name="errors-and-warnings"></a>Errores y advertencias

Las advertencias o errores que se producen indican problemas que se deben corregir antes de realizar implementaciones en Azure, como los ensamblados que faltan.

Si compila la aplicación, la ejecuta localmente mediante el emulador de proceso o la publica en Azure, puede que aparezca el error: "La ruta de acceso especificada, el nombre de archivo o ambos son demasiado largos". Este error indica que la longitud del nombre completo de proyecto de Azure excede de 146 caracteres. Para corregir el problema, mueva la solución a una carpeta diferente con una ruta de acceso más corta.

Para obtener más información sobre cómo tratar las advertencias como errores, consulte [Configuración de un proyecto de servicio en la nube de Azure con Visual Studio](vs-azure-tools-configuring-an-azure-project.md).

### <a name="test-the-migration-locally"></a>Prueba local de la migración

1. En el **Explorador de soluciones** de Visual Studio, haga clic con el botón derecho en el proyecto de servicio en la nube agregado y seleccione **Establecer como proyecto de inicio**.
1. Seleccione **Depurar > Iniciar depuración** (F5) para iniciar el entorno de depuración de Azure. Este entorno proporciona específicamente la emulación de varios servicios de Azure.

### <a name="use-an-azure-sql-database-for-your-application"></a>Uso de una instancia de SQL Database Azure para su aplicación

Si tiene una cadena de conexión para la aplicación web que usa una instancia local de SQL Server Database, debe migrar la base de datos a Azure SQL Database en su lugar y actualizar la cadena de conexión. Para obtener instrucciones con este proceso, consulte los temas siguientes:

- [Migración de una base de datos de SQL Server a una instancia de SQL Database en la nube](/azure/sql-database/sql-database-cloud-migrate)
- [Uso de .NET (C#) con Visual Studio para conectarse a una instancia de Azure SQL Database y consultarla](/azure/sql-database/sql-database-connect-query-dotnet-visual-studio).

## <a name="publish-the-application-to-azure-cloud-service"></a>Publicación de la aplicación en un Servicio en la nube de Azure

1. Cree el servicio en la nube y las cuentas de almacenamiento necesarias en la suscripción de Azure según se describe en [Preparación para publicar o implementar una aplicación de Azure desde Visual Studio](vs-azure-tools-cloud-service-publish-set-up-required-services-in-visual-studio.md).
1. En Visual Studio, haga clic con el botón derecho en el proyecto de aplicación y seleccione **Publicar en Microsoft Azure...** (que es distinto del comando "Publicar...").
1. En la ventana **Publicar aplicación de Azure** que aparece, inicie sesión mediante la cuenta de la suscripción de Azure y seleccione **Siguiente >**.
1. En la pestaña **Configuración > Configuración común**, seleccione el servicio en la nube de destino en la lista desplegable **Servicio en la nube**, junto con las configuraciones y el entorno elegidos.
1. En **Configuración > Configuración avanzada**, seleccione la cuenta de almacenamiento que desea usar y después seleccione **Siguiente >**.
1. En **Diagnósticos**, seleccione si desea enviar información a Application Insights.
1. Seleccione **Siguiente >** para ver un resumen y después seleccione **Publicar** para iniciar la implementación.
1. Visual Studio abre una ventana de registro de actividad donde puede realizar un seguimiento del progreso:

    ![VST_AzureActivityLog](./media/vs-azure-tools-migrate-publish-web-app-to-cloud-service/IC744149.png)

1. (Opcional) Para cancelar el proceso de implementación, haga clic con el botón derecho en el elemento de línea del registro de actividad y después seleccione **Cancelar y quitar**. Este comando detiene el proceso de implementación y elimina el entorno de implementación de Azure. Nota: Para quitar este entorno de implementación una vez implementado, debe usar [Azure Portal](https://portal.azure.com).
1. (Opcional) Una vez iniciadas las instancias de rol, Visual Studio muestra automáticamente el entorno de implementación en el nodo **Explorador de servidores > Cloud Services**. Desde aquí puede ver el estado de las instancias de rol individuales.
1. Para tener acceso a la aplicación después de la implementación, elija la flecha situada junto a la implementación cuando aparezca un estado **Completado** en el **registro de actividad de Azure** junto con la dirección URL. Vea la tabla siguiente para obtener detalles acerca de cómo iniciar un tipo específico de aplicación web desde Azure.

## <a name="using-the-compute-emulator-and-starting-application-in-azure"></a>Uso del emulador de proceso e inicio de la aplicación en Azure

Todos los tipos de aplicación se pueden iniciar en un explorador conectado al depurador de Visual Studio; para ello, seleccione **Depurar > Iniciar depuración** (F5). Con un proyecto de aplicación web ASP.NET vacía, primero debe agregar una página `.aspx` en la aplicación y establecerla como la página de inicio del proyecto web.

En la tabla siguiente se proporciona información detallada sobre cómo iniciar la aplicación en Azure:

   | Tipo de aplicación web | Ejecución en Azure |
   | --- | --- | --- |
   | Aplicación web ASP.NET<br/>(incluidos MVC 2, MVC 3 y MVC 4) | Seleccione la dirección URL en la pestaña **Implementación** del **registro de actividad de Azure**. |
   | Aplicación web ASP.NET vacía | Si tiene una página `.aspx` predeterminada en la aplicación, seleccione la dirección URL en la pestaña **Implementación** del **registro de actividad de Azure**. Para navegar a otra página distinta, escriba una dirección URL con el siguiente formato en un explorador: `<deployment_url>/<page_name>.aspx` |
   | Aplicación de Silverlight<br/>Aplicación de negocios de Silverlight<br/>Aplicación de navegación de Silverlight | Navegue hasta la página específica de la aplicación con el siguiente formato de dirección URL: `<deployment_url>/<page_name>.aspx` |
    Aplicación del servicio de WCF<br/>Aplicación de servicio de flujo de trabajo de WCF | Establezca el archivo `.svc` como la página de inicio del proyecto de servicio WCF. A continuación, vaya a `<deployment_url>/<service_file>.svc`. |
   | Entidades dinámicas de ASP.NET<br/>Linq to SQL de datos dinámicos de ASP.NET | Actualice la cadena de conexión como se describe en la siguiente sección. A continuación, vaya a `<deployment_url>/<page_name>.aspx`. Para Linq to SQL, debe usar una instancia de Azure SQL Database. |

## <a name="update-a-connection-string-for-aspnet-dynamic-entities"></a>Actualizar una cadena de conexión para Entidades dinámicas de ASP.NET

1. Cree una instancia de SQL Azure Database para una aplicación web de Entidades dinámicas de ASP.NET como se describió anteriormente en (#use-an-azuresql-database-for-your-application).
1. Agregue las tablas y los campos que necesite para esta base de datos desde Azure Portal.
1. Especifique una cadena de conexión en el archivo `web.config` con el siguiente formato y guarde el archivo:

    ```xml
    <addname="tempdbEntities"connectionString="metadata=res://*/Model1.csdl|res://*/Model1.ssdl|res://*/Model1.msl;provider=System.Data.SqlClient;provider connection string=&quot;data source=<server name>\SQLEXPRESS;initial catalog=<database name>;integrated security=True;multipleactiveresultsets=True;App=EntityFramework&quot;"providerName="System.Data.EntityClient"/>
    ```

    Actualice el valor *connectionString* con la cadena de conexión de ADO.NET para la Base de datos SQL Azure de la manera siguiente:

    ```xml
    XMLCopy<addname="tempdbEntities"connectionString="metadata=res://*/Model1.csdl|res://*/Model1.ssdl|res://*/Model1.msl;provider=System.Data.SqlClient;provider connection string=&quot;Server=tcp:<SQL Azure server name>.database.windows.net,1433;Database=<database name>;User ID=<user name>;Password=<password>;Trusted_Connection=False;Encrypt=True;multipleactiveresultsets=True;App=EntityFramework&quot;"providerName="System.Data.EntityClient"/>
    ```

## <a name="supported-project-templates"></a>Plantillas de proyecto compatibles

Las aplicaciones que se pueden migrar y publicar en Cloud Services deben usar una de las plantillas de la tabla siguiente. No se admite ASP.NET Core.

| Grupo de plantillas | Plantilla de proyecto |
| --- | --- |
| Web | Aplicación web ASP.NET (.NET Framework) |
| Web | Aplicación web MVC 2 de ASP.NET |
| Web | Aplicación web MVC 3 de ASP.NET |
| Web | Aplicación web MVC 4 de ASP.NET |
| Web | Aplicación web ASP.NET vacía (o sitio) |
| Web | Aplicación web MVC 2 de ASP.NET vacía |
| Web | Aplicación web de Entidades de datos dinámicos de ASP.NET |
| Web | Aplicación web Linq to SQL de datos dinámicos de ASP.NET |
| Silverlight | Aplicación de Silverlight |
| Silverlight | Aplicación de negocios de Silverlight |
| Silverlight | Aplicación de navegación de Silverlight |
| WCF | Aplicación de servicio de WCF |
| WCF | Aplicación de servicio de flujo de trabajo de WCF |
| Flujo de trabajo | Aplicación de servicio de flujo de trabajo de WCF |

## <a name="next-steps"></a>Pasos siguientes

- [Preparación para publicar o implementar una aplicación de Azure desde Visual Studio](vs-azure-tools-cloud-service-publish-set-up-required-services-in-visual-studio.md)
- [Configuración de credenciales de autenticación con nombre](vs-azure-tools-setting-up-named-authentication-credentials.md)
