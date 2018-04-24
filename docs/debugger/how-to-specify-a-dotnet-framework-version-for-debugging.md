---
title: 'Cómo: especificar una versión de .NET Framework para la depuración | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- .NET Framework, specifying version for debugging
- debugging [Visual Studio], specifying .NET Framework version
ms.assetid: 7a4893ba-4620-4774-893f-378d4ca28893
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 2cb8da54b53814e7f044c67855e8071c627cf2e1
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-specify-a-net-framework-version-for-debugging"></a>Cómo: Especificar una versión de .NET Framework para la depuración
El depurador de [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] puede depurar versiones anteriores de Microsoft [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] así como la versión actual. Si inicia una aplicación desde Visual Studio, el depurador siempre puede identificar la versión correcta de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] para la aplicación que está depurando. Si la aplicación ya se está ejecutando y usa **adjuntar a**, el depurador no podrá siempre identificar una versión anterior de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Si esto ocurre, aparecerá un mensaje de error que indica,  
  
 El depurador ha deducido de manera equivocada la versión de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] que va a utilizar la aplicación.  
  
 En estos raros casos, puede establecer una clave del Registro para indicar al depurador qué versión utilizar.  
  
### <a name="to-specify-a-net-framework-version-for-debugging"></a>Para especificar una versión de .NET Framework para la depuración  
  
1.  Examine el directorio Windows\Microsoft.NET\Framework para encontrar las versiones de .NET Framework instaladas en su equipo. Los números de versión tienen un aspecto similar al siguiente:  
  
     `V1.1.4322`  
  
     Identifique el número de versión correcto y anótelo.  
  
2.  Iniciar el **Editor del registro** (regedit).  
  
3.  En el **Editor del registro**, abra la carpeta HKEY_LOCAL_MACHINE.  
  
4.  Desplácese a: HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine\\{449EC4CC-30D2-4032-9256-EE18EB41B62B}  
  
     Si la clave no existe, haga clic en HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine y haga clic en **nueva clave**. Nombre de la nueva clave `{449EC4CC-30D2-4032-9256-EE18EB41B62B}`.  
  
5.  Después de navegar a {449EC4CC-30D2-4032-9256-EE18EB41B62B}, busque en el **nombre** columna y encuentre la clave CLRVersionForDebugging.  
  
    1.  Si la clave no existe, haga clic en {449EC4CC-30D2-4032-9256-EE18EB41B62B} y haga clic en **nuevo valor de cadena**. A continuación, haga clic en el nuevo valor de cadena, haga clic en **cambiar el nombre de**y el tipo de `CLRVersionForDebugging`.  
  
6.  Haga doble clic en **CLRVersionForDebugging**.  
  
7.  En el **Editar cadena** , escriba el número de versión de .NET Framework en el **valor** cuadro. Por ejemplo: V1.1.4322  
  
8.  Haga clic en **Aceptar**.  
  
9. Cerrar la **Editor del registro**.  
  
     Si todavía obtiene un mensaje de error cuando empieza a depurar, compruebe que ha escrito correctamente el número de versión en el Registro. Compruebe también que está utilizando una versión de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] admitida por Visual Studio. El depurador es compatible con la versión actual de .NET Framework y con las versiones anteriores, pero puede no serlo con versiones futuras.  
  
## <a name="see-also"></a>Vea también  
 [Configuración y preparación de la depuración](../debugger/debugger-settings-and-preparation.md)