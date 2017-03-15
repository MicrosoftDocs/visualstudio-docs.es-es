---
title: "Soluci&#243;n de problemas de excepciones: errores de compilaci&#243;n de Cordova | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BLD102"
  - "BLD10205"
  - "BLD301"
  - "BLD401"
  - "BLDErr_Build_NodeMissing"
  - "BLDErr_BLD_Win8Required"
ms.assetid: 781c09e3-0704-4b30-9230-036cbdb2dff9
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
---
# Soluci&#243;n de problemas de excepciones: errores de compilaci&#243;n de Cordova
En este tema se describen algunos de los mensajes de error más comunes que se pueden ver al usar Visual Studio Tools para Apache Cordova.  
  
-   [MSBUILD: error de compilación de Cordova BLD102: No existe ese archivo o directorio 'config.xml'](#BLD102)  
  
-   [MSBUILD: error de compilación de Cordova BLD301: No se configuró ningún agente de compilación de iOS remoto](#BLD301)  
  
-   [MSBUILD: error de compilación de Cordova BLD401: No se encontró el módulo &lt;nombreDeMódulo&gt;](#BLD401)  
  
-   [MSBUILD: error de compilación de Cordova BLD10205: Instale el destino de Android](#BLD10205)  
  
-   [BLDErr_Build_NodeMissing La ruta al ejecutable Node.js no se pudo determinar](#BLDErr_Build_NodeMissing)  
  
-   [BLDErr_Build_Win8Required](#BLDErr_Build_Win8Required)  
  
 Si necesita ayuda más general sobre cómo solucionar errores en la aplicación Cordova, consulte la información sobre cómo [resolver errores de compilación](https://taco.visualstudio.com/en-us/docs/resolving-build-errors/).  
  
##  <a name="BLD102"></a> MSBUILD: error de compilación de Cordova BLD102: No existe ese archivo o directorio 'config.xml'  
 Si ve este error, asegúrese de que el proyecto incluya un archivo config.xml en la raíz del proyecto y compruebe que el proyecto está en el equipo local y no reside en un recurso compartido de red.  
  
 Para obtener más información, consulte esta [entrada de StackOverflow](http://stackoverflow.com/questions/27134007/new-cordova-project-gives-the-error-bld00102-no-such-file-or-directory-confi).  
  
##  <a name="BLD301"></a> MSBUILD: error de compilación de Cordova BLD301: No se configuró ningún agente de compilación de iOS remoto  
 La cadena de error completa es esta:  
  
-   MSBUILD: error de compilación de Cordova BLD301: No se configuró ningún agente de compilación de iOS remoto. Configúrelo en Herramientas \> Opciones \> Herramientas para Apache Cordova \> Configuración de agente remoto. Encontrará detalles y alternativas en http:\/\/go.microsoft.com\/fwlink\/?LinkID\=511904  
  
 Para obtener información sobre cómo instalar y configurar el agente de compilación remoto para iOS, consulte la [guía de configuración de iOS.](http://taco.visualstudio.com/en-us/docs/ios-guide/)  
  
##  <a name="BLD401"></a> MSBUILD: error de compilación de Cordova BLD401: No se encontró el módulo \<nombreDeMódulo\>  
 La cadena de error completa es esta:  
  
-   MSBUILD: error de compilación de Cordova BLD401: Error: BLD00401: No se encontró el módulo \<nombreDeMódulo\>. Vaya a Herramientas \-\-\> Opciones \-\-\> Herramientas para Apache Cordova \-\-\> Herramientas de Cordova \-\-\> Borrar la caché de Cordova y pruebe a compilar de nuevo.  
  
 Puede que sea necesario borrar la memoria caché y volver a instalar vs\-tac. Para obtener más información, consulte la información relativa a cómo [volver a instalar vs\-tac](http://taco.visualstudio.com/en-us/docs/configure-vs-tools-apache-cordova#vstac).  
  
 Después de borrar la caché, elimine la carpeta de plataformas del proyecto. Después, intente volver a compilar.  
  
##  <a name="BLD10205"></a> MSBUILD: error de compilación de Cordova BLD10205: Instale el destino de Android  
 Si ve este error, asegúrese de instalar las dependencias necesarias para el dispositivo de destino seleccionado mediante el Administrador de Android SDK \(SDK Manager.exe\).  
  
 Para obtener más información sobre el nivel de API requerido y otros componentes de Android SDK, consulte la información sobre cómo [instalar dependencias manualmente](http://taco.visualstudio.com/en-us/docs/configure-vs-tools-apache-cordova#ThirdParty).  
  
 También debe comprobar la ubicación que Visual Studio usa para encontrar Android SDK. Para ello, consulte la información sobre cómo [invalidar variables de entorno del sistema](http://taco.visualstudio.com/en-us/docs/configure-vs-tools-apache-cordova#env-var).  
  
 Para obtener más información sobre cómo instalar los componentes correctos para usar las herramientas, consulte la sección sobre [herramientas de terceros](http://taco.visualstudio.com/en-us/docs/install-vs-tools-apache-cordova#choose).  
  
##  <a name="BLDErr_Build_NodeMissing"></a> BLDErr\_Build\_NodeMissing La ruta al ejecutable Node.js no se pudo determinar  
 Si se ha instalado Node.js en una ubicación no predeterminada, Visual Studio podría no encontrarla. Vuelva a instalar Node.js en la ubicación predeterminada. Para obtener más información, consulte esta [entrada de StackOverflow](http://stackoverflow.com/questions/32203992/vs2015-cordova-apps-blderr-build-nodemissing) y este artículo sobre cómo [actualizar Node.js de forma segura](http://taco.visualstudio.com/en-us/docs/change-node-version/).  
  
##  <a name="BLDErr_Build_Win8Required"></a> BLDErr\_Build\_Win8Required  
 Se requiere Windows 8.1 para establecer Windows como destino en una aplicación creada con Visual Studio Tools para Apache Cordova.