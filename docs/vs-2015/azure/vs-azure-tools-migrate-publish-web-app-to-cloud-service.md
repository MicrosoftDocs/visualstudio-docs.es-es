---
title: Cómo migrar y publicar una aplicación Web a un servicio de nube de Azure desde Visual Studio | Microsoft Docs
description: Obtenga información sobre cómo migrar y publicar la aplicación web a un servicio de nube de Azure mediante Visual Studio
author: ghogen
manager: douge
ms.assetid: 9394adfd-a645-4664-9354-dd5df08e8c91
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/10/2017
ms.author: ghogen
ms.openlocfilehash: c122b54a4e22285678d13213cc73d6492baba629
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2018
ms.locfileid: "51003045"
---
# <a name="how-to-migrate-and-publish-a-web-application-to-an-azure-cloud-service-from-visual-studio"></a>Cómo: migrar y publicar una aplicación Web a un servicio de nube de Azure desde Visual Studio

Para aprovechar los servicios de hospedaje y escalabilidad de Azure, es posible que desee migrar e implementar la aplicación web a un servicio de nube de Azure. Se requieren cambios mínimos. Este artículo trata sobre la implementación de servicios en la nube para App Service, consulte [implementar una aplicación web en Azure App Service](/azure/app-service/app-service-deploy-local-git).

> [!Important]
> Esta migración solo se admite para los proyectos ASP.NET, Silverlight, WCF y flujo de trabajo de WCF específicos. No se admite para proyectos de ASP.NET Core. Consulte [plantillas de proyecto compatibles](#supported-project-templates).

## <a name="migrate-a-project-to-cloud-services"></a>Migrar un proyecto de servicios en la nube

1. Haga clic en el proyecto de aplicación web y seleccione **convertir > convertir en proyecto de servicio de nube de Microsoft Azure**. (Tenga en cuenta que este comando no aparece si ya tiene un proyecto de rol web en la solución).
1. Visual Studio crea un proyecto de servicio en la nube en la solución que contiene el rol web necesario. El nombre de este proyecto es el mismo que el proyecto de aplicación más el sufijo `.Azure`.
1. Visual Studio también establece la **Copy Local** propiedad en true para todos los ensamblados que son necesarios para MVC 2, MVC 3, MVC 4 y las aplicaciones de negocios de Silverlight. Esta propiedad agrega estos ensamblados al paquete de servicio que se usa para la implementación.

   > [!Important]
   > Si tiene otros ensamblados o archivos que son necesarios para esta aplicación web, debe establecer manualmente las propiedades de estos archivos. Para obtener información sobre cómo establecer estas propiedades, vea [incluir archivos en el paquete de servicio](#include-files-in-the-service-package).

### <a name="errors-and-warnings"></a>Errores y advertencias

Las advertencias o errores que se producen indican problemas para corregirlos antes de implementar en Azure, como los ensamblados que faltan.

Si cree su aplicación, ejecuta localmente mediante el emulador de proceso o publicarlo en Azure, puede ver el error: "la ruta de acceso especificada, el nombre de archivo o ambos son demasiado largos." Este error indica que la longitud del nombre completo del proyecto Azure excede de 146 caracteres. Para corregir el problema, mueva la solución a una carpeta diferente con una ruta más corta.

Para obtener más información acerca de cómo tratar las advertencias como errores, vea [configurar un proyecto de servicio de nube de Azure con Visual Studio](vs-azure-tools-configuring-an-azure-project.md).

### <a name="test-the-migration-locally"></a>Prueba local de la migración

1. En Visual Studio **el Explorador de soluciones**, haga clic en el proyecto de servicio en la nube agregado y seleccione **establecer como proyecto de inicio**.
1. Seleccione **Depurar > Iniciar depuración** (F5) para iniciar el entorno de depuración de Azure. Este entorno proporciona específicamente la emulación de varios servicios de Azure.

### <a name="use-an-azure-sql-database-for-your-application"></a>Usar una base de datos de SQL Azure para su aplicación

Si tiene una cadena de conexión para la aplicación web que usa una base de datos de SQL Server local, debe migrar la base de datos a Azure SQL Database en su lugar y actualizar la cadena de conexión. Para obtener instrucciones con este proceso, consulte los temas siguientes:

- [Migración de base de datos de SQL Server a SQL Database en la nube](/azure/sql-database/sql-database-cloud-migrate)
- [Uso de .NET (C#) con la base de datos de SQL Azure y Visual Studio para conectarse y consultar](/azure/sql-database/sql-database-connect-query-dotnet-visual-studio).

## <a name="publish-the-application-to-azure-cloud-service"></a>Publicar la aplicación en Azure Cloud Service

1. Creación de la nube es necesaria cuentas de servicio y almacenamiento en su suscripción de Azure como se describe en [preparación para publicar o implementar una aplicación de Azure desde Visual Studio](vs-azure-tools-cloud-service-publish-set-up-required-services-in-visual-studio.md).
1. En Visual Studio, haga clic en el proyecto de aplicación y seleccione **publicar en Microsoft Azure...**  (que es diferente del comando "Publicar …".).
1. En el **publicar aplicación de Azure** que aparece, inicie sesión con la cuenta con su suscripción de Azure y seleccione **siguiente >**.
1. En el **configuración > configuración común** pestaña, seleccione el servicio de nube de destino desde el **servicio en la nube** la lista desplegable, junto con su entorno concreto y configuraciones. 
1. En **configuración > Configuración avanzada**, seleccione la cuenta de almacenamiento que desea usar y después seleccione **siguiente >**.
1. En **diagnósticos**, elija si desea enviar información a Application Insights.
1. Seleccione **siguiente >** para ver un resumen, a continuación, seleccione **publicar** para iniciar la implementación.
1. Visual Studio abre una ventana de registro de actividad donde puede seguir el progreso:

    ![VST_AzureActivityLog](./media/vs-azure-tools-migrate-publish-web-app-to-cloud-service/IC744149.png)

1. (Opcional) Para cancelar el proceso de implementación, haga clic en el elemento de línea en el registro de actividad y elija **Cancelar y quitar**. Este comando detiene el proceso de implementación y elimina el entorno de implementación de Azure. Nota: para quitar este entorno de implementación una vez se ha implementado, debe usar el [portal Azure](https://portal.azure.com).
1. (Opcional) Después de que hayan iniciado las instancias de rol, Visual Studio muestra automáticamente el entorno de implementación en el **Explorador de servidores > Cloud Services** nodo. Desde aquí puede ver el estado de las instancias de rol individuales.
1. Para obtener acceso a la aplicación después de la implementación, elija la flecha situada junto a la implementación al estado **completado** aparece en el **registro de actividad de Azure** junto con la dirección URL. Consulte la tabla siguiente para obtener los detalles sobre cómo iniciar un tipo específico de la aplicación web de Azure.

## <a name="using-the-compute-emulator-and-starting-application-in-azure"></a>Mediante el emulador de proceso e iniciar la aplicación en Azure

Todos los tipos de aplicación se pueden iniciar en un explorador conectado al depurador de Visual Studio seleccionando **Depurar > Iniciar depuración** (F5). Con un proyecto de aplicación Web ASP.NET vacía, debe agregar primero un `.aspx` página en la aplicación y establecerla como página de inicio para el proyecto web.

En la tabla siguiente se proporciona detalles acerca de cómo iniciar la aplicación en Azure:

   | Tipo de aplicación Web | Que se ejecuta en Azure |
   | --- | --- | --- |
   | Aplicación web ASP.NET<br/>(incluidos MVC 2, MVC 3, MVC 4) | Seleccione la dirección URL en el **implementación** la pestaña para el **registro de actividad de Azure**. |
   | Aplicación Web ASP.NET vacía | Si tiene un valor predeterminado `.aspx` en la aplicación, seleccione la dirección URL en el **implementación** la pestaña para el **registro de actividad de Azure**. Para navegar a otra página, escriba una dirección URL de la forma siguiente en un explorador: `<deployment_url>/<page_name>.aspx` |
   | Aplicación de Silverlight<br/>Aplicación de negocios de Silverlight<br/>Aplicación de navegación de Silverlight | Vaya a la página específica de la aplicación con el formato de dirección URL siguiente: `<deployment_url>/<page_name>.aspx` |
    Aplicación del servicio de WCF<br/>Aplicación de servicio de flujo de trabajo de WCF | Establecer el `.svc` archivo como la página de inicio para el proyecto de servicio WCF. A continuación, vaya a `<deployment_url>/<service_file>.svc` |
   | Entidades dinámicas de ASP.NET<br/>Linq to SQL datos dinámicos de ASP.NET | Actualice la cadena de conexión como se describe en la sección siguiente. A continuación, vaya a `<deployment_url>/<page_name>.aspx`. Para Linq to SQL, debe usar una base de datos SQL de Azure. |

## <a name="update-a-connection-string-for-aspnet-dynamic-entities"></a>Actualizar una cadena de conexión para entidades dinámicas de ASP.NET

1. Cree una base de datos de SQL Azure para una aplicación web de entidades dinámicas de ASP.NET como se describe anteriormente en (#use-an-azuresql-database-for-your-application).
1. Agregue las tablas y los campos que necesite para esta base de datos desde el portal de Azure.
1. Especifique una cadena de conexión en el `web.config` con el siguiente formato de archivo y guarde el archivo:

    ```xml
    <addname="tempdbEntities"connectionString="metadata=res://*/Model1.csdl|res://*/Model1.ssdl|res://*/Model1.msl;provider=System.Data.SqlClient;provider connection string=&quot;data source=<server name>\SQLEXPRESS;initial catalog=<database name>;integrated security=True;multipleactiveresultsets=True;App=EntityFramework&quot;"providerName="System.Data.EntityClient"/>
    ```

    Actualización de la *connectionString* valor con la cadena de conexión de ADO.NET para la base de datos de SQL Azure como sigue:

    ```xml
    XMLCopy<addname="tempdbEntities"connectionString="metadata=res://*/Model1.csdl|res://*/Model1.ssdl|res://*/Model1.msl;provider=System.Data.SqlClient;provider connection string=&quot;Server=tcp:<SQL Azure server name>.database.windows.net,1433;Database=<database name>;User ID=<user name>;Password=<password>;Trusted_Connection=False;Encrypt=True;multipleactiveresultsets=True;App=EntityFramework&quot;"providerName="System.Data.EntityClient"/>
    ```

## <a name="supported-project-templates"></a>Plantillas de proyecto compatibles

Las aplicaciones que se pueden migrar y publicar en cloud services deben usar una de las plantillas en la tabla siguiente. No se admite ASP.NET Core.

| Grupo de plantillas | Plantilla de proyecto |
| --- | --- |
| Web | Aplicación Web ASP.NET (.NET Framework) |
| Web | Aplicación Web ASP.NET MVC 2 |
| Web | Aplicación Web ASP.NET MVC 3 |
| Web | Aplicación Web de ASP.NET MVC4 |
| Web | Aplicación Web ASP.NET vacía (o sitio) |
| Web | Aplicación Web vacía de ASP.NET MVC 2 |
| Web | Aplicación Web de entidades de datos dinámicos de ASP.NET |
| Web | Linq to SQL Web Application datos dinámicos de ASP.NET |
| Silverlight | Aplicación de Silverlight |
| Silverlight | Aplicación de negocios de Silverlight |
| Silverlight | Aplicación de navegación de Silverlight |
| WCF | Aplicación del servicio de WCF |
| WCF | Aplicación de servicio de flujo de trabajo de WCF |
| Flujo de trabajo | Aplicación de servicio de flujo de trabajo de WCF |

## <a name="next-steps"></a>Pasos siguientes

- [Preparación para publicar o implementar una aplicación de Azure desde Visual Studio](vs-azure-tools-cloud-service-publish-set-up-required-services-in-visual-studio.md)
- [Configuración de las credenciales de autenticación con nombre](vs-azure-tools-setting-up-named-authentication-credentials.md).
