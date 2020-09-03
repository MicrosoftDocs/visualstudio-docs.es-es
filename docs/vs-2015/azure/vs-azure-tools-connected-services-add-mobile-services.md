---
title: Agregar Mobile Services mediante Servicios conectados
description: Adición de Mobile Services mediante el cuadro de diálogo Agregar servicios conectados de Visual Studio
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
ms.openlocfilehash: 0a8f6fab3c8f30834a467e2ad98843b16a9245b4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "75916709"
---
# <a name="adding-mobile-services-by-using-visual-studio-connected-services"></a>Adición de Mobile Services mediante Servicios conectados de Visual Studio
Con Visual Studio 2015, puede conectarse a Azure Mobile Services usando el cuadro de diálogo **Agregar servicio conectado** . Puede conectarse desde cualquier aplicación cliente de C#, cualquier aplicación de JavaScript o cualquier aplicación de Cordova multiplataforma. Una vez conectado, puede crear y tener acceso a datos, crear API personalizadas y trabajos programados o agregar compatibilidad con notificaciones de inserción.  La operación de servicios conectados agrega todas las referencias adecuadas y el código de conexión. También puede aprovechar la compatibilidad integrada para la autenticación con diferentes esquemas de identidad populares, como cuentas de Microsoft, Azure AD, Facebook y Twitter.

## <a name="supported-project-types"></a>Tipos de proyecto compatibles
> [!NOTE]
> En Visual Studio 2015, la adición de Azure Mobile Services a proyectos universales de Windows (Windows 10) con el cuadro de diálogo Agregar servicios conectados no es compatible. Puede agregar Azure Mobile Services instalando los paquetes adecuados con el Administrador de paquetes NuGet de su proyecto.
>
>

Puede usar el cuadro de diálogo Servicios conectados para conectarse a Azure Mobile Services en los siguientes tipos de proyecto.

* Proyectos de la Tienda Windows 8.1 de .NET, Phone y aplicación universal
* Proyectos de la Tienda Windows 8.1 de JavaScript, Phone y aplicación universal
* Proyectos creados con herramientas de Visual Studio para Apache Cordova

## <a name="connect-to-azure-mobile-services-using-the-add-connected-services-dialog"></a>Conectarse a Azure Mobile Services con el cuadro de diálogo Agregar servicios conectados
1. Asegúrese de que tiene una cuenta de Azure. Si no tiene una cuenta de Azure, puede registrarse para obtener una [evaluación gratuita](https://azure.microsoft.com/pricing/free-trial/).
2. Abra el cuadro de diálogo **Agregar servicios conectados** .

   * En las aplicaciones .NET, abra el proyecto en Visual Studio, abra el menú contextual del nodo **Referencias** en el Explorador de soluciones y luego elija **Agregar servicio conectado**.

        ![Conexión a servicio móvil de Azure](./media/vs-azure-tools-connected-services-add-mobile-services/IC797635.png)
   * En los proyectos de aplicación Apache Cordova, abra el proyecto en Visual Studio, abra el menú contextual del nodo del proyecto en el Explorador de soluciones y luego elija **Agregar servicio conectado**.
3. En el cuadro de diálogo **Agregar servicio conectado**, seleccione **Servicios móviles de Azure** y, a continuación, elija el botón **Configurar**. Es posible que se le pida que inicie sesión en Azure si aún no lo ha hecho.

    ![Adición de un servicio móvil de Azure](./media/vs-azure-tools-connected-services-add-mobile-services/IC797636.png)
4. En el cuadro de diálogo **Servicios móviles de Azure**, seleccione un servicio móvil existente si dispone de uno. Si necesita crear un servicio móvil de Azure, siga el procedimiento indicado a continuación para ello. Si no, continúe con el paso siguiente.

    Para crear una cuenta de servicio móvil:

   1. Elija el vínculo **Crear servicio**, situado en la parte inferior del cuadro de diálogo.
       ![Agregar nuevo servicio conectado móvil](./media/vs-azure-tools-connected-services-add-mobile-services/IC797637.png)
   2. En el cuadro de diálogo **Crear servicio móvil**, puede elegir un servicio móvil de back-end de JavaScript o bien un servicio móvil de back-end de .NET de la lista desplegable **Tiempo de ejecución**.

       ![Creación de un servicio móvil](./media/vs-azure-tools-connected-services-add-mobile-services/IC797638.png)

       Un servicio de back-end de JavaScript es sencillo y eficaz. Si crea un servicio móvil de back-end de JavaScript, el código JavaScript del servidor se almacena en la nube, pero pueden editarse scripts del servidor mediante el Explorador de servidores o el Portal de administración de Azure.

       Un servicio móvil de back-end de .NET le ofrece todo el potencial y flexibilidad de API web y Entity Framework. Si crea un servicio móvil de back-end de .NET, se crea un proyecto para usted y se agrega a su solución.
   3. Elija la **región** en la que desea el servicio móvil y, a continuación, escriba un nombre de usuario y una contraseña para el servidor.
   4. Después de haber especificado toda la información necesaria, elija el botón **Crear** para crear el servicio móvil.
   5. El nuevo servicio móvil debe aparecer en la lista de servicios del cuadro de diálogo **Azure Mobile Services** . Elija el nuevo servicio móvil de la lista y, a continuación, elija el botón **Agregar** para agregar el servicio al proyecto.
5. Revise la página Introducción que aparece y consulte cómo se ha modificado el proyecto. Una página Introducción aparece en el explorador siempre que se agregue un servicio conectado. Puede revisar los pasos siguientes sugeridos y los ejemplos de código, o pasar a la página ¿Qué ha ocurrido? para ver qué referencias se agregaron al proyecto y cómo se han modificado los archivos de configuración y códigos.
6. Con los ejemplos de código como guía, comience a escribir código para tener acceso a su servicio móvil.

## <a name="next-steps"></a>Pasos siguientes
Formule preguntas y obtenga ayuda:

* [Foro de MSDN: Azure Mobile Services](https://social.msdn.microsoft.com/forums/azure/home?forum=azuremobile)
* [Azure Mobile Services en el blog del equipo de Microsoft Azure](https://azure.microsoft.com/blog/topics/mobile/)
* [Azure Mobile Services en azure.microsoft.com](https://azure.microsoft.com/services/mobile-services/)
* [Documentación de Azure Mobile Services en azure.microsoft.com](https://azure.microsoft.com/documentation/services/mobile-services/)
