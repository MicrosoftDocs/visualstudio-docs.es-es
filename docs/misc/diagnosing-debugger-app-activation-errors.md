---
title: "Diagnosticar errores de activaci&#243;n de aplicaciones del depurador | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.app_activation_failure"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 558ddc6d-0952-4617-84b8-0838717febcc
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "susanno"
manager: "douge"
---
# Diagnosticar errores de activaci&#243;n de aplicaciones del depurador
Se podrían mostrar uno de los siguientes errores si se intenta iniciar una aplicación de la Tienda Windows en el depurador de Visual Studio:  
  
 **8061**  
  
```  
Unable to activate Windows Store app 'AppName'. The ProcessName process started, but the activation request failed with error 'ErrorNumber'  
```  
  
 **8062**  
  
```  
Unable to activate Windows Store app 'AppName'. The activation request failed with error 'ErrorNumber'  
```  
  
## Para diagnosticar estos errores  
 No hay métodos seguros para corregir estos errores.  Utilice estas técnicas para diagnosticar el problema.  
  
### Usar el visor de eventos  
  
1.  Abra el visor de eventos \(en el menú Inicio de Windows, busque **Visor de eventos**\).  Abra el visor de eventos y, en el árbol, vaya a la carpeta **Application and Services Log\\Microsoft\\Windows\\Apps**.  
  
2.  Filtre la vista a los identificadores de eventos: 5900\-6000  
  
3.  Examinar el registro y comprobar qué ocurrió.  
  
### Usar el depurador nativo  
 Configurar el proyecto para que se ejecute en un depurador nativo.  
  
 En Visual Studio, establezca el **Tipo de depurador** en **Solo nativo** en la página **Depurar** \(**Depuración** en C\+\+ y JavaScript\) de las páginas de propiedades del proyecto de inicio.  
  
 Consulte las excepciones producidas examinando la ventana de salida.  Quizás desee configurar el depurador para que se detenga cuando se produzcan estas excepciones.  
  
## Corrección de errores de licencia de aplicación  
 Podría recibir un mensaje de activación que indica que “esta aplicación no se abrió porque hay un problema con su licencia”. Puede probar una de estas soluciones:  
  
-   En el menú **Compilar**, elija **Limpiar solución**, abra la carpeta de soluciones en el Explorador de archivos y elimine las carpetas **bin** y **obj**.  A continuación, elija **Compilar** y **Recompilar solución**.  La recompilación de la solución crea las carpetas necesarias.  
  
-   Seleccione la aplicación en la pantalla Inicio y, a continuación, elija Desinstalar en la barra de la aplicación.  Limpie y recompile la solución.  
  
-   Desde un símbolo del sistema que se esté ejecutando con privilegios de administrador, use comandos de Powershell para quitar y volver a instalar la licencia de desarrollador.  Limpie y recompile la solución.  Vea [Obtención de una licencia de desarrollador \(aplicaciones de la Tienda\)](http://msdn.microsoft.com/library/windows/apps/Hh974578.aspx#getting_a_developer_license_at_a_command_prompt).