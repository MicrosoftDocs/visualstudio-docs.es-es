---
title: 'Cómo: especificar una versión de .NET Framework para la depuración | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68176561"
---
# <a name="how-to-specify-a-net-framework-version-for-debugging"></a>Cómo: Especificar una versión de .NET Framework para la depuración
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El depurador de [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] puede depurar versiones anteriores de Microsoft [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] así como la versión actual. Si inicia una aplicación desde Visual Studio, el depurador siempre puede identificar la versión correcta de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] para la aplicación que se está depurando. Si la aplicación ya se está ejecutando y se usa **asociar a**, es posible que el depurador no siempre pueda identificar una versión anterior de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . Si esto ocurre, aparecerá un mensaje de error que indica,  
  
 El depurador ha deducido de manera equivocada la versión de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] que va a utilizar la aplicación.  
  
 En estos raros casos, puede establecer una clave del Registro para indicar al depurador qué versión utilizar.  
  
### <a name="to-specify-a-net-framework-version-for-debugging"></a>Para especificar una versión de .NET Framework para la depuración  
  
1. Examine el directorio Windows\Microsoft.NET\Framework para encontrar las versiones de .NET Framework instaladas en su equipo. Los números de versión tienen un aspecto similar al siguiente:  
  
     `V1.1.4322`  
  
     Identifique el número de versión correcto y anótelo.  
  
2. Inicie el **Editor del Registro** (regedit).  
  
3. En el **Editor del Registro**, abra la carpeta HKEY_LOCAL_MACHINE.  
  
4. Vaya a: HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine\\{449EC4CC-30D2-4032-9256-EE18EB41B62B}  
  
     Si la clave no existe, haga clic con el botón derecho en HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine y haga clic en **Nueva clave**. Asigne el nombre `{449EC4CC-30D2-4032-9256-EE18EB41B62B}` a la nueva clave.  
  
5. Después de navegar a {449EC4CC-30D2-4032-9256-EE18EB41B62B }, examine la columna **Nombre** y encuentre la clave CLRVersionForDebugging.  
  
    1. Si la clave no existe, haga clic con el botón derecho en {449EC4CC-30D2-4032-9256-EE18EB41B62B} y haga clic en **Nuevo valor de cadena**. Después, haga clic con el botón derecho en el nuevo valor de cadena, haga clic en **Cambiar nombre** y escriba `CLRVersionForDebugging`.  
  
6. Haga doble clic en **CLRVersionForDebugging**.  
  
7. En el cuadro **Editar cadena**, escriba el número de versión de .NET Framework en el cuadro **Valor**. Por ejemplo: V1.1.4322  
  
8. Haga clic en **Aceptar**.  
  
9. Cierre el **Editor del Registro**.  
  
     Si todavía obtiene un mensaje de error cuando empieza a depurar, compruebe que ha escrito correctamente el número de versión en el Registro. Compruebe también que está utilizando una versión de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] admitida por Visual Studio. El depurador es compatible con la versión actual de .NET Framework y con las versiones anteriores, pero puede no serlo con versiones futuras.  
  
## <a name="see-also"></a>Consulte también  
 [Configuración y preparación de la depuración](../debugger/debugger-settings-and-preparation.md)
