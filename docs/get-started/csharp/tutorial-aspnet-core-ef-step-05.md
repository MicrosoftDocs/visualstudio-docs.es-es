---
title: 'Paso 5: Implementación de la aplicación de ASP.NET Core en Azure'
description: Implemente la aplicación web de ASP.NET Core en Azure con este tutorial en vídeo y con instrucciones detalladas.
ms.custom: get-started
ms.date: 08/14/2020
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
monikerRange: vs-2019
ms.topic: tutorial
ms.devlang: CSharp
author: ardalis
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 55dd48ed2c319984fcc96e806c97a7ae24ce7170
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2020
ms.locfileid: "88248667"
---
# <a name="step-5-deploy-your-aspnet-core-app-to-azure"></a>Paso 5: Implementación de la aplicación de ASP.NET Core en Azure

Siga estos pasos para implementar la aplicación de ASP.NET Core y su base de datos en Azure.

_Vea este vídeo y siga el tutorial para implementar su primera aplicación de ASP.NET Core en Azure_.

> [!VIDEO https://www.youtube.com/embed/n8wz_f5_4wI]

## <a name="open-your-project"></a>Apertura del proyecto

Abra la aplicación de ASP.NET Core en Visual Studio 2019. La aplicación ya debe usar la configuración con EF Core y una API web de trabajo, con la configuración establecida en el [paso 4 de esta serie de tutoriales](tutorial-aspnet-core-ef-step-04.md).

## <a name="publish-to-azure-app-service"></a>Publicación en Azure App Service

1. Haga clic con el botón derecho en el proyecto en el Explorador de soluciones y elija **Publicar**. En el asistente para **publicar**, elija **Azure** como destino.

   ![Captura de pantalla de Azure App Service 1](media/vs-2019/app-service-screen-1.png)

1. Para el destino específico, elija **Azure App Service (Windows)** .

   ![Captura de pantalla de Azure App Service 2](media/vs-2019/app-service-screen-2.png)

1. Seleccione **Cree su aplicación del Servicio de aplicaciones de Azure**. Si aún no tiene una cuenta de Azure, haga clic en **Crear una cuenta de Azure gratis** y complete el breve proceso de registro.

   ![Captura de pantalla de Azure App Service 3](media/vs-2019/app-service-screen-3.png)

1. Especifique un nombre y un grupo de recursos, o acepte los valores predeterminados y elija **Crear**. Un grupo de recursos es simplemente una forma de organizar los recursos relacionados en Azure, como los servicios que funcionan junto con cuentas de almacenamiento, almacenes de claves y bases de datos.

   ![Captura de pantalla de Azure App Service 4](media/vs-2019/app-service-screen-4.png)

1. Elija **Finalizar**. Se crean los recursos en Azure, se implementa la aplicación y la pestaña **Publicar** se rellena con la información sobre lo que acaba de crear. La pestaña **Publicar** proporciona un botón para publicar con un solo clic con la misma configuración, muestra los detalles de la configuración o permite agregar servicios, como por ejemplo, una base de datos.

Ahora, agregue una base de datos de Azure SQL Server.

1. En la pestaña **Publicar**, en **Dependencias de servicio**, junto a **Base de datos de SQL Server**, elija **Configurar**.

1. En la siguiente pantalla, elija **Azure SQL Database**.

   ![Captura de pantalla de Azure SQL Database](media/vs-2019/app-service-azure-sql-db.png)

1. En la pantalla **Configurar base de datos SQL**, seleccione **Crear una base de datos SQL**.

   ![Captura de pantalla de Configurar base de datos SQL](media/vs-2019/app-service-azure-sql-db-2.png)

1. En la pantalla **Azure SQL Database: Crear nuevo**, cree un nuevo servidor de base de datos.

   ![Captura de pantalla de Azure SQL Database: Crear nuevo](media/vs-2019/app-service-azure-sql-db-3.png)

1. En la pantalla **SQL Server: Crear nuevo**, elija un nombre y una ubicación, y especifique un nombre de usuario y una contraseña de administrador.

   ![Crear servidor SQL Server en Visual Studio de 2019](media/vs-2019/app-service-azure-sql-db-overlayed.png)

## <a name="exploring-the-azure-portal-and-your-hosted-app"></a>Exploración de Azure Portal y de la aplicación hospedada

Una vez creada la instancia de App Service, el sitio se iniciará en un explorador. Mientras se carga, también puede encontrar la instancia de App Service en Azure Portal. Con la exploración de las opciones disponibles para la instancia de App Service, encontrará una sección **Introducción** donde puede iniciar y detener la aplicación.

![Opciones de Azure App Service](media/vs-2019/vs2019-azure-app-service-menu-options.png)

### <a name="scalability"></a>Escalabilidad

Puede examinar las opciones para escalar la aplicación vertical y horizontalmente. La escalabilidad vertical se refiere a aumentar los recursos disponibles para cada instancia que hospeda la aplicación. La escalabilidad horizontal se refiere a aumentar el número de instancias que hospedan la aplicación. Puede configurar el escalado automático de la aplicación, lo que aumentará automáticamente el número de instancias que se utilizan para hospedar la aplicación en respuesta a la carga y, después, lo reducirá una vez que la carga disminuya.

### <a name="security-and-compliance"></a>Seguridad y cumplimiento normativo

Otra ventaja de hospedar nuestra aplicación en Azure es la seguridad y el cumplimiento. Azure App Service cumple con las normas ISO, SOC y PCI. También podemos elegir entre autenticar a los usuarios con Azure Active Directory o con inicios de sesión en redes sociales como Twitter, Facebook, Google o Microsoft. Podemos crear restricciones de direcciones IP, administrar identidades de servicio, agregar dominios personalizados y admitir SSL para la aplicación, así como configurar copias de seguridad con copias de archivo restaurables de la base de datos, la configuración y el contenido de la aplicación. A estas características se puede acceder desde las opciones de menú Autenticación/autorización, Identidad, Copias de seguridad y Configuración de SSL.

### <a name="deployment-slots"></a>Ranuras de implementación

Con frecuencia, al implementar una aplicación, hay un breve período de tiempo de inactividad mientras se reinicia la aplicación. Las ranuras de implementación evitan este problema, ya que permiten implementar una instancia de almacenamiento provisional independiente o un conjunto de instancias y prepararlas antes de que pasen a producción. Esta transición consiste simplemente en un redireccionamiento del tráfico instantáneo y directo. Si se presenta algún problema en producción después de la transición, siempre puede volver al último estado de producción bien conocido.

## <a name="update-connection-string"></a>Actualización de la cadena de conexión

De forma predeterminada, Azure espera que la conexión de una nueva aplicación a su nueva base de datos de SQL Server use una cadena de conexión denominada `DefaultConnection`. Actualmente, la aplicación creada anteriormente en esta serie de tutoriales usa una cadena de conexión llamada `AppDbContext`. Necesitamos cambiar esto en *appsettings.json* y *Startup.cs* y, después, volver a implementar la aplicación.

## <a name="test-the-app-running-in-azure"></a>Prueba de la aplicación que se ejecuta en Azure

Vaya a la ruta de acceso */Games*, donde debe agregar un juego nuevo y ver que aparece en la lista. A continuación, vaya a la ruta de acceso */swagger*, desde donde debe usar los puntos de conexión de la API web para confirmar que la API de la aplicación también funciona.

¡Enhorabuena! Ha completado esta serie de tutoriales en vídeo.

## <a name="next-steps"></a>Pasos siguientes

Obtenga más información sobre cómo diseñar aplicaciones de ASP.NET Core con estos recursos gratuitos.

[Arquitectura de una aplicación de ASP.NET Core](https://dotnet.microsoft.com/learn/web/aspnet-architecture)

## <a name="see-also"></a>Consulte también

- [Publicar una aplicación de ASP.NET Core en Azure con Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?view=aspnetcore-2.2)