---
title: 'Cómo: responder al depurador Just-In-Time | Documentos de Microsoft'
ms.custom: ''
ms.date: 05/23/17
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c506e12fc8e6637e2b53852587e6a37c57cbf5ce
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-respond-to-the-just-in-time-debugger"></a>Cómo: responder al depurador Just-In-Time

Las acciones que debe realizar cuando vea Just-in-Time cuadro de diálogo de depurador dependen de qué desea hacer:

#### <a name="if-you-want-to-fix-or-debug-the-error-visual-studio-users"></a>Si desea corregir o depurar el error (los usuarios de Visual Studio)

- Debe tener [instalado Visual Studio](https://www.microsoft.com/en-us/download/details.aspx?id=48146) para ver la información detallada sobre el error e intenta depurarlo. Para obtener más información, consulte [depurar con el depurador Just](../debugger/debug-using-the-just-in-time-debugger.md). Si no se puede resolver el error y corregir la aplicación, póngase en contacto con el propietario de la aplicación para resolver el error.

#### <a name="if-you-want-to-prevent-the-just-in-time-debugger-dialog-box-from-appearing"></a>Si desea impedir que aparezca el cuadro de diálogo de depurador Just

Puede tomar medidas para evitar Just-in-Time cuadro de diálogo de depurador que aparezcan. Si el error encarga de la aplicación, puede ejecutar la aplicación normalmente.

1. (Aplicaciones web) Si desea ejecutar una aplicación web, puede deshabilitar la depuración de script.

    Para Internet Explorer o Microsoft Edge, deshabilitar la depuración de scripts en el cuadro de diálogo Opciones de Internet. Puede tener acceso a esta configuración de la **el Panel de Control** > **red e Internet** > **opciones de Internet** (los pasos exactos dependen de su versión de Windows y el explorador).

    ![JITInternetOptions](../debugger/media/jitinternetoptions.png "JITInternetOptions")

    A continuación, vuelva a abrir la página web donde se encuentra el error. Si cambia la configuración, el problema no se soluciona, póngase en contacto con el propietario de la aplicación web para corregir el problema.

3. (Los usuarios de visual Studio) Si tiene instalado Visual Studio (o si ha instalado anteriormente y quitó), [Just-in-Time de deshabilitar la depuración](../debugger/debug-using-the-just-in-time-debugger.md) e intente volver a ejecutar la aplicación.

    > [!IMPORTANT]
    > Si deshabilita Just-in-Time de depuración y la aplicación encuentra una excepción no controlada (error), ya sea un cuadro de diálogo de error estándar en su lugar verá o la aplicación se bloqueará o de bloqueo. La aplicación no se ejecutará normalmente hasta que se solucione el error (por usted o el propietario de la aplicación).

2. (ASP.NET e IIS) Si hospeda una aplicación Web ASP.NET en IIS, deshabilite la depuración de servidor.

    En el Administrador de IIS, haga clic en el nodo del servidor y elija **cambiar a vista características**. En la sección de ASP.NET, elija **compilación de .NET** y, a continuación, asegúrese de que elige **False** como el comportamiento de depuración (los pasos son diferentes en versiones anteriores de IIS).
  
## <a name="see-also"></a>Vea también    
 [Conceptos básicos del depurador](../debugger/debugger-basics.md)   
