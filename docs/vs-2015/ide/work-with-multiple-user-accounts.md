---
title: Trabajar con varias cuentas de usuario | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: b73c865c-74e0-420e-89cc-43524f4aafd0
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d4f53d723ca9249386027264038df6c5895b7d03
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60081234"
---
# <a name="work-with-multiple-user-accounts"></a>Trabajar con varias cuentas de usuario
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si tiene varias cuentas de Microsoft y/o cuentas profesionales o educativas, puede agregarlas todas a Visual Studio para que pueda acceder a los recursos desde cualquier cuenta sin tener que iniciar sesión separadamente. En la fecha RTM de Visual Studio 2015, los servicios de Azure, Application Insights, Team Foundation Server y Office 365 admiten la experiencia de inicio de sesión simplificada. Más adelante pueden hacerse disponibles otros servicios.  
  
 Después de agregar varias cuentas en un equipo, el conjunto de cuentas lo acompañará si inicia sesión en Visual Studio desde otro equipo. Es importante tener en cuenta que, aunque los nombres de cuenta tienen movilidad, las credenciales no. Por lo tanto, se le pedirá que escriba las credenciales de las otras cuentas la primera vez que intente usar sus recursos en el nuevo equipo.  
  
 En este tutorial enseñamos a agregar varias cuentas de Visual Studio y a ver los recursos accesibles desde esas cuentas reflejados en sitios como el cuadro de diálogo **Agregar servicio conectado** , **Explorador de servidores**y **Team Explorer**.  
  
#### <a name="sign-in-to-visual-studio"></a>Iniciar sesión en Visual Studio  
  
1. Inicie sesión en Visual Studio 2015 con una cuenta Microsoft o una cuenta profesional. Debería ver su nombre de usuario reflejado en la esquina superior derecha de la ventana, tal como se muestra:  
  
     ![Usuario registrado actualmente](../ide/media/vs2015-username.png "VS2015_UserName")  
  
### <a name="access-your-azure-account-in-server-explorer"></a>Obtener acceso a su cuenta de Azure en el Explorador de servidores  
 Presione **Ctrl + Alt + S** para abrir **Explorador de servidores**. Haga clic en el icono de Azure y, cuando se expanda, debería ver los recursos disponibles en la cuenta de Azure que está asociada con el identificador que usó para iniciar sesión en Visual Studio 2015. Debería tener este aspecto, solo que son sus recursos los que se verían y no los del Sr. Guido:  
  
 ![El Explorador de servidores mostrando el nodo de Azure Tools expandido](../ide/media/vs2015-serverexplorer.png "VS2015_ServerExplorer")  
  
 La primera vez que use Visual Studio en cualquier dispositivo específico, el cuadro de diálogo solo mostrará las suscripciones registradas en el Id. con el que ha iniciado sesión en el IDE. Puede acceder a los recursos de cualquiera de las demás cuentas directamente desde el **Explorador de servidores** : haga clic con el botón secundario en el nodo de Azure, elija **Administrar y filtrar suscripciones** y, luego, agregue las cuentas desde el control de selector de cuenta. Si lo desea, después puede elegir otra cuenta haciendo clic en la flecha hacia abajo y eligiendo en la lista de cuentas. Después de elegir la cuenta, puede indicar qué suscripciones de esa cuenta desea mostrar en el Explorador de servidores.  
  
 ![Administrar el cuadro de diálogo Suscripciones de Azure](../ide/media/vs2015-manage-subs.png "vs2015_manage_subs")  
  
 La próxima vez que abra el Explorador de servidores, se mostrarán los recursos de esas suscripciones.  
  
### <a name="access-your-azure-account-via-add-connected-service-dialog"></a>Obtener acceso a su cuenta de Azure a través del cuadro de diálogo Agregar servicio conectado  
  
1. Cree un proyecto de aplicación universal en C#.  
  
2. Haga clic con el botón derecho en el nodo de proyecto en el Explorador de soluciones y seleccione **Agregar > Servicio conectado**. El asistente Agregar servicio conectado aparece y muestra la lista de los servicios de la cuenta de Azure que está asociada con su id. de inicio de sesión de Visual Studio. No tiene que iniciar sesión por separado en Azure. Sin embargo, deberá iniciar sesión en las otras cuentas la primera vez que intente acceder a sus recursos desde un equipo determinado.  
  
    > [!WARNING]
    >  Si se trata de la primera vez que va a crear una aplicación de Store en Visual Studio 2015 en un equipo específico, se le pedirá que habilite el dispositivo para el modo de desarrollo yendo a **configuración &#124; . Actualizaciones y seguridad &#124; para desarrolladores** en el equipo. Para obtener más información, vea [Habilitar el dispositivo para el desarrollo](https://msdn.microsoft.com/library/windows/apps/dn706236.aspx).  
  
### <a name="access_azure"></a> Obtener acceso a Azure Active Directory en un proyecto web  
 Azure AD ofrece compatibilidad para el inicio de sesión único de usuario final en las aplicaciones web ASP.NET MVC o autenticación AD en los servicios web de API. La autenticación de dominio es diferente de la autenticación de cuentas de usuario individuales; los usuarios que tienen acceso a su dominio de Active Directory pueden usar sus cuentas de Azure AD existentes para conectarse a sus aplicaciones web. Las aplicaciones de Office 365 también pueden utilizar la autenticación de dominio. Para ver esto en funcionamiento, cree una aplicación web (**Archivo > Nuevo proyecto > C# > Nube > Aplicación web ASP.NET**). En el cuadro de diálogo Nuevo proyecto ASP.NET, elija **Cambiar autenticación**. El Asistente para autenticación aparece y le permite elegir qué tipo de autenticación se utilizará en la aplicación.  
  
 ![Cuadro de diálogo Cambiar autenticación para ASP.NET](../ide/media/vs2015-change-authentication.png "VS2015_change_authentication")  
  
 Para obtener más información sobre los diferentes tipos de autenticación en ASP.NET, consulte [Creating ASP.NET Web Projects in Visual Studio 2013](http://www.asp.net/visual-studio/overview/2013/creating-web-projects-in-visual-studio#orgauth) (la información sobre autenticación sigue siendo pertinente para Visual Studio 2015).  
  
### <a name="access-your-visual-studio-team-services-account"></a>Obtener acceso a la cuenta de Visual Studio Team Services  
 En el menú principal, seleccione **Equipo > Conectar con Team Foundation Server** para mostrar la ventana **Team Explorer**. Haga clic en **Seleccionar proyectos de equipo**y luego, en el cuadro de lista, en **Seleccionar Team Foundation Server**, debería ver la dirección URL de su cuenta de Visual Studio Team Services. Cuando seleccione la dirección URL, se iniciará sesión sin tener que volver a escribir las credenciales.  
  
## <a name="add-a-second-user-account-to-visual-studio"></a>Agregar una segunda cuenta de usuario a Visual Studio  
 Haga clic en la flecha hacia abajo que hay al lado de su nombre de usuario en la esquina superior derecha de Visual Studio. Luego haga clic en el elemento de menú **Configuración de la cuenta** . Aparece el cuadro de diálogo **Administrador de cuentas** y muestra la cuenta con la que inició sesión. Haga clic en el vínculo **Agregar una cuenta** en la esquina inferior izquierda del cuadro de diálogo para agregar una cuenta de Microsoft o una cuenta profesional o educativa nuevas.  
  
 ![Selector de cuentas de Visual Studio](../ide/media/vs2015-acct-picker.png "VS2015_acct_picker")  
  
 Siga los avisos para escribir las credenciales de la cuenta nueva. La ilustración siguiente muestra el Administrador de cuentas después de que un usuario haya agregado su cuenta profesional de Contoso.com.  
  
 ![Administrador de cuentas](../ide/media/vs2015-accountmanager.gif "VS2015_AccountManager")  
  
## <a name="revisit-the-add-connected-services-wizard-and-server-explorer"></a>Volver a visitar el asistente Agregar servicios conectados y Explorador de servidores  
 Vaya ahora al **Explorador de servidores** y haga de nuevo doble clic en el nodo de Azure y elija **Administrar y filtrar suscripciones**. Elija la nueva cuenta, haga clic en la flecha desplegable junto a la cuenta actual y elija las suscripciones que desea mostrar en el Explorador de servidores. Debería ver todos los servicios asociados a la suscripción especificada. Aunque no tenga iniciada sesión en el IDE de Visual Studio con la segunda cuenta, ha iniciado sesión en los servicios y recursos de esa cuenta. Lo mismo sirve para **Proyecto > Agregar servicio conectado** y **Equipo > Conectar con Team Foundation Server**.
