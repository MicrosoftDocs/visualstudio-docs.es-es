---
title: "C&#243;mo: Anular el registro de VSPackages | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "aplicaciones de ejemplo [SDK de Visual Studio], desinstalar"
  - "configurar, VSPackages"
ms.assetid: b51522f0-c033-4d93-b928-2171a953032b
caps.latest.revision: 14
caps.handback.revision: 14
manager: "douge"
---
# C&#243;mo: Anular el registro de VSPackages
De forma predeterminada, cuando se compilan VSPackages, se registran en el subárbol del registro experimental. El subárbol experimental se puede llenar de VSPackages que no tiene previsto conservar una vez que haya experimentado con ellos.  
  
 Para eliminar todos los paquetes que están registrados en el subárbol experimental, simplemente restablezca el subárbol mediante la herramienta CreateExpInstance con la opción \/Reset. Para obtener más información, consulta [La instancia Experimental](../extensibility/the-experimental-instance.md).  
  
## Anular el registro de VSPackages individuales  
  
#### Para anular el registro de un VSPackage no administrado  
  
1.  Haga clic en **Inicio** y en **Ejecutar**, escriba `regsvr32 /u` *pathToVSPackage.dll* y, a continuación, haga clic en Aceptar.  
  
 Dado que los VSPackages no administrados contienen código de registro automático, puede usar la utilidad regsvr32 para regístrarlos y anular su registro.  
  
#### Para anular el registro de un VSPackage administrado  
  
1.  Haga clic en **Inicio** y en **Ejecutar**, escriba la *ruta de instalación del SDK de Visual Studio*`\EnvSDK\tools\bin\x86\regpkg /unregister` *pathToVSPackage.dll* y, a continuación, haga clic en Aceptar.  
  
 La herramienta RegPkg lee los atributos de registro que se pueden incrustar en un VSPackage administrado. El conmutador **\/unregister** indica a RegPkg elimine la información del registro.  
  
## Vea también  
 [Visual Studio Integration Samples](http://msdn.microsoft.com/es-es/b5dbf078-3af2-4fed-a1ea-171e4ee73a43)