---
title: 'Cómo: responder al depurador Just-In-Time | Microsoft Docs'
ms.custom: ''
ms.date: 05/23/17
ms.technology: vs-ide-debug
ms.topic: troubleshooting
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5cec8887ddf2023a8abd08f409b93f47efdc7001
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/19/2018
ms.locfileid: "39155573"
---
# <a name="how-to-respond-to-the-just-in-time-debugger"></a>Cómo: responder al depurador Just-In-Time

Las acciones que debe realizar cuando vea Just-in-Time cuadro de diálogo de depurador dependen de lo que está intentando hacer:

#### <a name="if-you-want-to-fix-or-debug-the-error-visual-studio-users"></a>Si desea corregir o depurar el error (usuarios de Visual Studio)

- Debe tener [instalado Visual Studio](http://visualstudio.microsoft.com) para ver la información detallada sobre el error y se intenta depurarla. Para obtener más información, consulte [depurar con el depurador Just In Time](../debugger/debug-using-the-just-in-time-debugger.md). Si no se puede resolver el error y corregir la aplicación, póngase en contacto con el propietario de la aplicación para resolver el error.

#### <a name="if-you-want-to-prevent-the-just-in-time-debugger-dialog-box-from-appearing"></a>Si desea evitar que aparezca el cuadro de diálogo de depurador Just In Time

Puede tomar medidas para evitar Just-in-Time cuadro de diálogo de depurador que aparezca. Si la aplicación controla el error, puede ejecutar la aplicación con normalidad.

1. (Aplicaciones web) Si intenta ejecutar una aplicación web, puede deshabilitar la depuración de scripts.

    Para Internet Explorer o Microsoft Edge, deshabilitar la depuración de scripts en el cuadro de diálogo Opciones de Internet. Puede tener acceso a estos valores desde el **Panel de Control** > **red e Internet** > **opciones de Internet** (los pasos exactos dependen de su versión de Windows y el explorador).

    ![JITInternetOptions](../debugger/media/jitinternetoptions.png "JITInternetOptions")

    A continuación, vuelva a abrir la página web donde encontró el error. Si cambia esta configuración no resuelve el problema, póngase en contacto con el propietario de la aplicación web para corregir el problema.

3. (Los usuarios de visual Studio) Si tiene instalado Visual Studio (o si ha instalado anteriormente y la ha quitado), [Just-in-Time de deshabilitar la depuración](../debugger/debug-using-the-just-in-time-debugger.md) e intente volver a ejecutar la aplicación.

    > [!IMPORTANT]
    > Si deshabilita Just-in-Time de depuración y la aplicación encuentra una excepción no controlada (error), verá un cuadro de diálogo de error estándar en su lugar, o la aplicación se bloquee o se bloqueará. La aplicación no se ejecutará con normalidad hasta que se ha corregido el error (por usted o el propietario de la aplicación).

2. (IIS y ASP.NET) Si va a hospedar una aplicación Web ASP.NET en IIS, deshabilite la depuración de servidor.

    En el Administrador de IIS, haga clic en el nodo de servidor y elija **cambiar a vista características**. En la sección ASP.NET, elija **compilación .NET** y, a continuación, asegúrese de elegir **False** como el comportamiento de depuración (los pasos son diferentes en versiones anteriores de IIS).

## <a name="see-also"></a>Vea también
 [Conceptos básicos del depurador](../debugger/debugger-basics.md)
