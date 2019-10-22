---
title: Adición de Mobile Services mediante Connected Services
description: Incorporación de Mobile Services mediante el cuadro de diálogo de Visual Studio agregar servicios conectados
documentationcenter: na
author: ghogen
manager: jillfra
ms.assetid: 75c3cb93-88e1-476d-a416-f34caa3608e3
ms.topic: conceptual
ms.workload: azure-vs
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.date: 12/16/2015
ms.author: mlearned
ms.openlocfilehash: 4bfda342952820b4472a1f826273a7b9075faa9a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62964002"
---
# <a name="adding-mobile-services-by-using-visual-studio-connected-services"></a>Adición de Mobile Services mediante Visual Studio Connected Services
Con Visual Studio 2015, puede conectarse a Azure Mobile Services mediante el **Agregar servicio conectado** cuadro de diálogo. Puede conectarse desde cualquier C# aplicación cliente, cualquier aplicación de JavaScript o aplicación de Cordova multiplataforma. Una vez conectado, puede crear y tener acceso a datos, crear API personalizadas y trabajos programados o agregar compatibilidad para notificaciones de inserción.  La operación de servicios conectados agrega todas las referencias adecuadas y el código de conexión. También puede aprovechar la compatibilidad integrada para la autenticación con una variedad de sistemas de identidad populares, como Azure AD, Facebook, Twitter y Microsoft Accounts.

## <a name="supported-project-types"></a>Tipos de proyecto compatibles
> [!NOTE]
> En Visual Studio 2015, no se admite agregar Azure Mobile Services a un proyecto Universal de Windows (Windows 10) mediante el cuadro de diálogo Agregar servicios conectados. Puede agregar Azure Mobile Services instalando los paquetes adecuados con el Administrador de paquetes de NuGet para el proyecto.
>
>

Puede usar el cuadro de diálogo servicios conectados para conectarse a Azure Mobile Services en los siguientes tipos de proyecto.

* Proyectos de .NET Windows 8.1 Store, Phone y aplicación Universal
* Proyectos Store de Windows 8.1 de JavaScript, Phone y aplicación Universal
* Proyectos creados con Visual Studio Tools para Apache Cordova

## <a name="connect-to-azure-mobile-services-using-the-add-connected-services-dialog"></a>Conectarse a Azure Mobile Services mediante el cuadro de diálogo Agregar servicios conectados
1. Asegúrese de que tiene una cuenta de Azure. Si no tienes una cuenta de Azure, puede suscribirse una [gratuita](http://go.microsoft.com/fwlink/?LinkId=518146).
2. Abra el **agregar servicios conectados** cuadro de diálogo.

   * Las aplicaciones. NET, abra el proyecto en Visual Studio, abra el menú contextual para el **referencias** nodo en el Explorador de soluciones y, a continuación, elija **Agregar servicio conectado**

        ![Conectarse al servicio móvil de Azure](./media/vs-azure-tools-connected-services-add-mobile-services/IC797635.png)
   * Para los proyectos de aplicación de Apache Cordova, abra el proyecto en Visual Studio, abra el menú contextual del nodo de proyecto en el Explorador de soluciones y, a continuación, elija **Agregar servicio conectado**.
3. En el **Agregar servicio conectado** diálogo cuadro, elija **Azure Mobile Services**y, a continuación, elija el **configurar** botón. Se pedirá que inicie sesión en Azure si aún no lo ha hecho.

    ![Adición de un servicio móvil de Azure](./media/vs-azure-tools-connected-services-add-mobile-services/IC797636.png)
4. En el **Azure Mobile Services** cuadro de diálogo, seleccione un servicio móvil existente si tiene uno. Si necesita crear un nuevo servicio móvil de Azure, siga el procedimiento siguiente para hacerlo. De lo contrario, vaya al paso siguiente.

    Para crear una nueva cuenta de servicio móvil:

   1. Elija la **Create Service** vínculo en la parte inferior del cuadro de diálogo.
       ![Agregar nuevo servicio conectado móvil](./media/vs-azure-tools-connected-services-add-mobile-services/IC797637.png)
   2. En el **crear servicio móvil** cuadro de diálogo, puede elegir un servicio móvil de back-end de JavaScript, o un servicio móvil de back-end de .NET desde el **en tiempo de ejecución** lista desplegable.

       ![Creación de un servicio móvil](./media/vs-azure-tools-connected-services-add-mobile-services/IC797638.png)

       Un servicio de back-end de JavaScript es sencillo y eficaz. Si crea un servicio móvil de back-end de JavaScript, el código de JavaScript del lado servidor se almacena en la nube, pero puede editar scripts de servidor utilizando el Explorador de servidores o el portal de administración de Azure.

       Un servicio móvil de back-end de .NET ofrece toda la potencia y flexibilidad de API Web y Entity Framework. Si crea un servicio móvil de back-end. NET, un proyecto se crea automáticamente y agrega a la solución.
   3. Elija la **región** donde desea que el servicio móvil y, a continuación, escriba un nombre de usuario y una contraseña para el servidor.
   4. Después de haber especificado toda la información necesaria, elija el **crear** botón para crear el servicio móvil.
   5. El nuevo servicio móvil debe aparecer en la lista de servicios en la **Azure Mobile Services** cuadro de diálogo. Elija el nuevo servicio móvil en la lista y, a continuación, elija el **agregar** botón para agregar el servicio al proyecto.
5. Revise la página de introducción que aparece y descubra cómo se ha modificado el proyecto. Una página Introducción aparece en el explorador cuando se agrega un servicio conectado. Puede revisar los pasos siguientes sugeridos y los ejemplos de código, o cambie a la página ¿Qué ha ocurrido para ver qué referencias se agregaron al proyecto y cómo se han modificado los archivos de código y la configuración.
6. Con los ejemplos de código como guía, empiece a escribir código para tener acceso a su servicio móvil.

## <a name="how-your-project-is-modified"></a>¿Cómo se modifica el proyecto?
Cómo Visual Studio modifica el proyecto depende del tipo de proyecto. Para C# las aplicaciones cliente, consulte [¿qué ha ocurrido? – C# proyectos](http://go.microsoft.com/fwlink/p/?LinkId=513119). Las aplicaciones cliente de JavaScript, consulte [¿qué ha ocurrido? – proyectos de JavaScript](http://go.microsoft.com/fwlink/p/?LinkId=513120). Las aplicaciones de Cordova, consulte [¿qué ha ocurrido? – proyectos Cordova](http://go.microsoft.com/fwlink/p/?LinkId=513116).

## <a name="next-steps"></a>Pasos siguientes
Formule preguntas y obtenga ayuda:

* [Foro de MSDN: Azure Mobile Services](https://social.msdn.microsoft.com/forums/azure/home?forum=azuremobile)
* [Azure Mobile Services en el blog del equipo de Microsoft Azure](https://azure.microsoft.com/blog/topics/mobile/)
* [Azure Mobile Services en azure.microsoft.com](https://azure.microsoft.com/services/mobile-services/)
* [Documentación de Azure Mobile Services en azure.microsoft.com](https://azure.microsoft.com/documentation/services/mobile-services/)
