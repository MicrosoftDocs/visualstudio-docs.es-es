---
title: "Utilizar Windows en tiempo de ejecuci&#243;n en JavaScript | Microsoft Docs"
ms.custom: ""
ms.date: "02/03/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "JavaScript, Windows en tiempo de ejecución"
ms.assetid: 90658546-f746-4e34-a7d1-71cf9ee322a2
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Utilizar Windows en tiempo de ejecuci&#243;n en JavaScript
Si usa JavaScript para escribir una aplicación de la [!INCLUDE[win8_appname_long](../javascript/includes/win8-appname-long-md.md)] o de la Tienda de Windows Phone, puede utilizar las clases, los métodos y las propiedades de Windows en tiempo de ejecución del mismo modo que utilizaría objetos, métodos y propiedades nativos de JavaScript.  En este tema se incluye información de introducción y vínculos a temas en los que se explican los conceptos básicos del uso de las API de Windows en tiempo de ejecución en JavaScript, incluida una explicación de cómo se representan los tipos de Windows en tiempo de ejecución, cómo se usan los métodos asincrónicos de Windows en tiempo de ejecución y cómos se escuchan y controlan los eventos de Windows en tiempo de ejecución.  
  
 La documentación de referencia de JavaScript se encuentra en [Referencia del lenguaje JavaScript](../javascript/javascript-language-reference.md).  
  
> [!IMPORTANT]
>  Las características de Windows en tiempo de ejecución no están disponibles para las aplicaciones que se ejecutan en Internet Explorer.  
  
## Documentación de referencia de Windows en tiempo de ejecución  
 Para obtener información de referencia sobre la documentación, vea [Windows Runtime reference](http://msdn.microsoft.com/es-es/8fe97dbf-8cd4-435f-b481-9e83d0519f9e).  Hay disponibles ejemplos de código en JavaScript y también en C\+\+, C\# y Visual Basic.  
  
## Escritura de componentes de Windows en tiempo de ejecución en C\+\+, C\# o Visual Basic  
 Si desea instrucciones para la escritura de componentes de Windows en tiempo de ejecución que se pueden usar en JavaScript, vea [Crear componentes de Windows en tiempo de ejecución en](../Topic/Creating%20Windows%20Runtime%20Components.md).  
  
## Convenciones sobre el uso de mayúsculas con características de Windows en tiempo de ejecución  
 Las convenciones sobre el uso de mayúsculas en características de Windows en tiempo de ejecución en JavaScript son ligeramente distintas de las de otros lenguajes:  
  
-   Los espacios de nombres y las clases están en estilo Pascal:  
  
    ```javascript  
    Windows.Deployment.PackageInfo;  
    ```  
  
-   Los miembros de clases, incluidos los métodos y las propiedades, así como los miembros de estructuras y enumeraciones, están en estilo Camel:  
  
    ```javascript  
    Deployment.PackageInfo.createPackage();  
    ```  
  
-   Los nombres de eventos están en minúscula:  
  
    ```javascript  
    dataTransferManager.ontargetapplicationchosen;  
    ```  
  
## Vea también  
 [Consideraciones al utilizar la API de Windows en tiempo de ejecución](../jswinrt/considerations-when-using-the-windows-runtime-api.md)   
 [Usar métodos asincrónicos de Windows en tiempo de ejecución](../jswinrt/using-windows-runtime-asynchronous-methods.md)   
 [Control de eventos de Windows en tiempo de ejecución en JavaScript](../jswinrt/handling-windows-runtime-events-in-javascript.md)   
 [Representación de JavaScript de tipos de Windows Runtime](../jswinrt/javascript-representation-of-windows-runtime-types.md)   
 [Proyección de JavaScript de DateTime y TimeSpan de Windows en tiempo de ejecución](../jswinrt/windows-runtime-datetime-and-timespan-representations.md)