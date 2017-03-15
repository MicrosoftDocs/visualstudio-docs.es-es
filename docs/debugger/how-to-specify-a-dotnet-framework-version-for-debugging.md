---
title: "C&#243;mo: Especificar una versi&#243;n de .NET Framework para la depuraci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - ".NET Framework, especificar una versión para la depuración"
  - "depurar [Visual Studio], especificar la versión de .NET Framework"
ms.assetid: 7a4893ba-4620-4774-893f-378d4ca28893
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C&#243;mo: Especificar una versi&#243;n de .NET Framework para la depuraci&#243;n
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El depurador de [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] puede depurar versiones anteriores de Microsoft [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] así como la versión actual.  Si inicia una aplicación desde Visual Studio, el depurador siempre puede identificar la versión correcta de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] para la aplicación que se está depurando.  Si la aplicación ya se está ejecutando y usa **Asociar a**, el depurador no siempre podrá identificar una versión anterior de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Si esto ocurre, aparecerá un mensaje de error que indica,  
  
 El depurador ha deducido de manera equivocada la versión de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] que va a utilizar la aplicación.  
  
 En estos raros casos, puede establecer una clave del Registro para indicar al depurador qué versión utilizar.  
  
### Para especificar una versión de .NET Framework para la depuración  
  
1.  Examine el directorio Windows\\Microsoft.NET\\Framework para encontrar las versiones de .NET Framework instaladas en su equipo.  Los números de versión tienen un aspecto similar al siguiente:  
  
     `V1.1.4322`  
  
     Identifique el número de versión correcto y anótelo.  
  
2.  Inicie el **Editor del Registro** \(regedit\).  
  
3.  En el **Editor del Registro**, abra la carpeta HKEY\_LOCAL\_MACHINE.  
  
4.  Navegue a: HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\VisualStudio\\10.0\\AD7Metrics\\Engine\\{449EC4CC\-30D2\-4032\-9256\-EE18EB41B62B}  
  
     Si la clave no existe, haga clic con el botón secundario en HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\VisualStudio\\10.0\\AD7Metrics\\Engine y haga clic en **Nueva clave**.  Asigne el nombre `{449EC4CC-30D2-4032-9256-EE18EB41B62B }` a la nueva clave.  
  
5.  Después de navegar a {449EC4CC\-30D2\-4032\-9256\-EE18EB41B62B }, examine la columna **Nombre** y encuentre la clave CLRVersionForDebugging.  
  
    1.  Si la clave no existe, haga clic con el botón secundario del mouse en {449EC4CC\-30D2\-4032\-9256\-EE18EB41B62B} y haga clic en **Nuevo valor de cadena**.  A continuación, haga clic con el botón secundario en el nuevo valor de cadena, haga clic en **Cambiar nombre** y escriba `CLRVersionForDebugging`.  
  
6.  Haga doble clic en **CLRVersionForDebugging**.  
  
7.  En el cuadro **Editar cadena**, escriba el número de versión de .NET Framework en el cuadro **Valor**.  Por ejemplo: V1.1.4322  
  
8.  Haga clic en **Aceptar**.  
  
9. Cierre el **Editor del Registro**.  
  
     Si todavía obtiene un mensaje de error cuando empieza a depurar, compruebe que ha escrito correctamente el número de versión en el Registro.  Compruebe también que está utilizando una versión de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] admitida por Visual Studio.  El depurador es compatible con la versión actual de .NET Framework y con las versiones anteriores, pero puede no serlo con versiones futuras.  
  
## Vea también  
 [Preparación y configuración de la depuración](../debugger/debugger-settings-and-preparation.md)