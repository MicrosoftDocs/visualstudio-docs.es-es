---
title: Agregar Mobile Services mediante Servicios conectados
description: Agregar Mobile Services mediante el cuadro de diálogo Agregar Servicios conectados de Visual Studio
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
ms.openlocfilehash: 4f84970daea03904d4642317cf6097beb07be7f1
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300184"
---
# <a name="adding-mobile-services-by-using-visual-studio-connected-services"></a>Agregar Mobile Services mediante Visual Studio Servicios conectados
Con Visual Studio 2015, puede conectarse a Azure Mobile Services mediante el cuadro de diálogo **Agregar servicio conectado** . Puede conectarse desde cualquier C# aplicación cliente, cualquier aplicación JavaScript o aplicación Cordova multiplataforma. Una vez conectado, puede crear y obtener acceso a los datos, crear API personalizadas y trabajos programados, o agregar compatibilidad para las notificaciones de extracción.  La operación servicios conectados agrega todas las referencias adecuadas y el código de conexión. También puede aprovechar la compatibilidad integrada para la autenticación con una variedad de esquemas de identidad populares, como Azure AD, Facebook, Twitter y cuentas de Microsoft.

## <a name="supported-project-types"></a>Tipos de proyecto admitidos
> [!NOTE]
> En Visual Studio 2015, no se admite la adición de Azure Mobile Services a proyectos universales de Windows (Windows 10) mediante el cuadro de diálogo Agregar Servicios conectados. Puede Agregar Azure Mobile Services instalando los paquetes correspondientes con el administrador de paquetes NuGet para el proyecto.
>
>

Puede usar el cuadro de diálogo Servicios conectados para conectarse a Azure Mobile Services en los siguientes tipos de proyecto.

* Proyectos de aplicaciones universales, de tienda y de .NET Windows 8.1
* Proyectos de aplicaciones universales, de tienda y de Windows 8.1 de JavaScript
* Proyectos creados con Visual Studio Tools para Apache Cordova

## <a name="connect-to-azure-mobile-services-using-the-add-connected-services-dialog"></a>Conexión a Azure Mobile Services mediante el cuadro de diálogo Agregar Servicios conectados
1. Asegúrese de que tiene una cuenta de Azure. Si no tiene una cuenta de Azure, puede registrarse para obtener una [evaluación gratuita](https://go.microsoft.com/fwlink/?LinkId=518146).
2. Abra el cuadro de diálogo **agregar servicios conectados** .

   * En el caso de las aplicaciones .NET, abra el proyecto en Visual Studio, abra el menú contextual del nodo **referencias** en explorador de soluciones y, a continuación, elija **Agregar servicio conectado** .

        ![Conexión al servicio móvil de Azure](./media/vs-azure-tools-connected-services-add-mobile-services/IC797635.png)
   * Para Apache Cordova proyectos de aplicación, abra el proyecto en Visual Studio, abra el menú contextual del nodo de proyecto en Explorador de soluciones y, a continuación, elija **Agregar servicio conectado**.
3. En el cuadro de diálogo **Agregar servicio conectado**, seleccione **Azure Mobile Services** y, a continuación, elija el botón **Configurar**. Es posible que se le pida que inicie sesión en Azure si todavía no lo ha hecho.

    ![Adición de un servicio móvil de Azure](./media/vs-azure-tools-connected-services-add-mobile-services/IC797636.png)
4. En el cuadro de diálogo **Azure Mobile Services**, seleccione un servicio móvil existente si dispone de uno. Si necesita crear un nuevo servicio móvil de Azure, siga el procedimiento que se indica a continuación. En caso contrario, vaya al paso siguiente.

    Para crear una nueva cuenta de servicio móvil:

   1. Elija el vínculo **Crear servicio**, situado en la parte inferior del cuadro de diálogo.
       ![agregar un nuevo servicio conectado móvil](./media/vs-azure-tools-connected-services-add-mobile-services/IC797637.png)
   2. En el cuadro de diálogo **crear servicio móvil** , puede elegir un servicio móvil de back-end de JavaScript o un servicio móvil de back-end de .net en la lista desplegable **tiempo de ejecución** .

       ![Creación de un servicio móvil](./media/vs-azure-tools-connected-services-add-mobile-services/IC797638.png)

       Un servicio back-end de JavaScript es sencillo y eficaz. Si crea un servicio móvil de back-end de JavaScript, el código de JavaScript del lado del servidor se almacena en la nube, pero puede editar los scripts del servidor mediante el Explorador de servidores o el Portal de administración de Azure.

       Un servicio móvil de back-end de .NET ofrece toda la eficacia y flexibilidad de la API Web y Entity Framework. Si crea un servicio móvil de back-end de .NET, se crea un proyecto y se agrega a la solución.
   3. Elija la **región** en la que desea el servicio móvil y, a continuación, escriba un nombre de usuario y una contraseña para el servidor.
   4. Después de haber especificado toda la información necesaria, elija el botón **Crear** para crear el servicio móvil.
   5. El nuevo servicio móvil debe aparecer en la lista de servicios del cuadro de diálogo **Mobile Services de Azure** . Elija el nuevo servicio móvil de la lista y, a continuación, elija el botón **Agregar** para agregar el servicio al proyecto.
5. Revise la página introducción que aparece y descubra cómo se ha modificado el proyecto. Aparece una página Introducción en el explorador cuando se agrega un servicio conectado. Puede revisar los pasos siguientes sugeridos y los ejemplos de código, o pasar a la página ¿Qué ha ocurrido? para ver qué referencias se agregaron al proyecto y cómo se han modificado los archivos de configuración y códigos.
6. Con los ejemplos de código como guía, empiece a escribir código para acceder a su servicio móvil.

## <a name="how-your-project-is-modified"></a>¿Cómo se modifica el proyecto?
El modo en que Visual Studio modifica el proyecto depende del tipo de proyecto. Para C# las aplicaciones cliente, consulte [¿qué C# ha ocurrido? – proyectos](https://go.microsoft.com/fwlink/p/?LinkId=513119). Para las aplicaciones cliente de JavaScript, consulte [¿Qué ha ocurrido? – proyectos de JavaScript](https://go.microsoft.com/fwlink/p/?LinkId=513120). Para las aplicaciones de Cordova, consulte [¿Qué ha ocurrido? – proyectos de Cordova](https://go.microsoft.com/fwlink/p/?LinkId=513116).

## <a name="next-steps"></a>Pasos siguientes
Formule preguntas y obtenga ayuda:

* [Foro de MSDN: Azure Mobile Services](https://social.msdn.microsoft.com/forums/azure/home?forum=azuremobile)
* [Azure Mobile Services en el blog del equipo de Microsoft Azure](https://azure.microsoft.com/blog/topics/mobile/)
* [Mobile Services de Azure en azure.microsoft.com](https://azure.microsoft.com/services/mobile-services/)
* [Documentación de Azure Mobile Services en azure.microsoft.com](https://azure.microsoft.com/documentation/services/mobile-services/)
