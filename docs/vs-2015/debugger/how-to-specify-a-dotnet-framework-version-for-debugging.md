---
title: Procedimiento Especificar una versión de .NET Framework para la depuración | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- .NET Framework, specifying version for debugging
- debugging [Visual Studio], specifying .NET Framework version
ms.assetid: 7a4893ba-4620-4774-893f-378d4ca28893
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4c785c419ead31ad90e2b20ae7f48af778598bb6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68176561"
---
# <a name="how-to-specify-a-net-framework-version-for-debugging"></a>Procedimiento Especificación de una versión de .NET Framework para la depuración
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El depurador de [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] puede depurar versiones anteriores de Microsoft [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] así como la versión actual. Si inicia una aplicación desde Visual Studio, el depurador siempre puede identificar la versión correcta de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] para la aplicación que se está depurando. Si ya se está ejecutando la aplicación y usa **adjuntar a**, el depurador no siempre puede identificar una versión anterior de la [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Si esto ocurre, aparecerá un mensaje de error que indica,  
  
 El depurador ha deducido de manera equivocada la versión de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] que va a utilizar la aplicación.  
  
 En estos raros casos, puede establecer una clave del Registro para indicar al depurador qué versión utilizar.  
  
### <a name="to-specify-a-net-framework-version-for-debugging"></a>Para especificar una versión de .NET Framework para la depuración  
  
1. Examine el directorio Windows\Microsoft.NET\Framework para encontrar las versiones de .NET Framework instaladas en su equipo. Los números de versión tienen un aspecto similar al siguiente:  
  
     `V1.1.4322`  
  
     Identifique el número de versión correcto y anótelo.  
  
2. Inicie el **Editor del Registro** (regedit).  
  
3. En el **Editor del Registro**, abra la carpeta HKEY_LOCAL_MACHINE.  
  
4. Vaya a: HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine\\{449EC4CC-30D2-4032-9256-EE18EB41B62B}  
  
     Si la clave no existe, haga clic con el botón derecho en HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine y haga clic en **Nueva clave**. Nombre de la nueva clave `{449EC4CC-30D2-4032-9256-EE18EB41B62B}`.  
  
5. Después de navegar a {449EC4CC-30D2-4032-9256-EE18EB41B62B }, examine la columna **Nombre** y encuentre la clave CLRVersionForDebugging.  
  
    1. Si la clave no existe, haga clic con el botón derecho en {449EC4CC-30D2-4032-9256-EE18EB41B62B} y haga clic en **Nuevo valor de cadena**. A continuación, haga clic en el nuevo valor de cadena, haga clic en **cambiar el nombre de**y el tipo `CLRVersionForDebugging`.  
  
6. Haga doble clic en **CLRVersionForDebugging**.  
  
7. En el cuadro **Editar cadena**, escriba el número de versión de .NET Framework en el cuadro **Valor**. Por ejemplo:  V1.1.4322  
  
8. Haga clic en **OK**.  
  
9. Cierre el **Editor del Registro**.  
  
     Si todavía obtiene un mensaje de error cuando empieza a depurar, compruebe que ha escrito correctamente el número de versión en el Registro. Compruebe también que está utilizando una versión de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] admitida por Visual Studio. El depurador es compatible con la versión actual de .NET Framework y con las versiones anteriores, pero puede no serlo con versiones futuras.  
  
## <a name="see-also"></a>Vea también  
 [Configuración y preparación de la depuración](../debugger/debugger-settings-and-preparation.md)
