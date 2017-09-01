---
title: Uso de Windows Runtime en JavaScript | Microsoft Docs
ms.custom: 
ms.date: 02/03/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JavaScript, Windows Runtime
ms.assetid: 90658546-f746-4e34-a7d1-71cf9ee322a2
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6fbf89668d47d55d1d77a1d7f11765567fc73405
ms.openlocfilehash: c81f5d83056ceb87987e263f09c0d5e5017dbb6f
ms.contentlocale: es-es
ms.lasthandoff: 08/11/2017

---
# <a name="using-the-windows-runtime-in-javascript"></a>Uso de Windows Runtime en JavaScript
Cuando escribe una aplicación de la Plataforma universal de Windows (UWP), puede utilizar las clases, los métodos y las propiedades de Windows Runtime del mismo modo que utilizaría objetos, métodos y propiedades nativos de JavaScript. En este tema se incluye información de introducción y vínculos a temas en los que se explican los conceptos básicos del uso de las API de Windows Runtime en JavaScript, incluida una explicación de cómo se representan los tipos de Windows Runtime, cómo se usan los métodos asincrónicos de Windows Runtime y cómos se escuchan y controlan los eventos de Windows Runtime.  
  
 Puede encontrar documentación de referencia de JavaScript en [JavaScript Language Reference](../javascript/javascript-language-reference.md) (Referencia del lenguaje JavaScript).  
  
> [!IMPORTANT]
>  Las características de Windows Runtime no están disponibles para las aplicaciones que se ejecutan en Internet Explorer.  
  
## <a name="windows-runtime-reference-documentation"></a>Documentación de referencia de Windows Runtime  
 Puede encontrar la documentación de referencia en [Windows Runtime Reference](https://msdn.microsoft.com/en-us/library/windows/apps/br211377.aspx) (Referencia de Windows Runtime). Hay disponibles ejemplos de código en JavaScript y también en C++, C# y Visual Basic.  
  
## <a name="writing-windows-runtime-components-in-c-c-or-visual-basic"></a>Escritura de componentes de Windows Runtime en C++, C# o Visual Basic  
 Para obtener instrucciones y directrices relativas a la escritura de componentes de Windows Runtime que pueden usarse en JavaScript, consulte [Crear componentes de Windows Runtime en C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp) y [Crear componentes de Windows Runtime en C# y Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic).  
  
## <a name="casing-conventions-with-windows-runtime-features"></a>Convenciones sobre el uso de mayúsculas con características de Windows Runtime  
 Las convenciones sobre el uso de mayúsculas en características de Windows en tiempo de ejecución en JavaScript son ligeramente distintas de las de otros lenguajes:  
  
-   Los espacios de nombres y las clases están en estilo Pascal:  
  
    ```JavaScript  
    Windows.Deployment.PackageInfo;  
    ```  
  
-   Los miembros de clases, incluidos los métodos y las propiedades, así como los miembros de estructuras y enumeraciones, están en estilo Camel:  
  
    ```JavaScript  
    Deployment.PackageInfo.createPackage();  
    ```  
  
-   Los nombres de eventos están en minúscula:  
  
    ```JavaScript  
    dataTransferManager.ontargetapplicationchosen;  
    ```  
  
## <a name="see-also"></a>Vea también  
 [Consideraciones al usar la API de Windows Runtime](../jswinrt/considerations-when-using-the-windows-runtime-api.md)   
 [Uso de métodos asincrónicos de Windows Runtime](../jswinrt/using-windows-runtime-asynchronous-methods.md)   
 [Control de eventos de Windows Runtime en JavaScript](../jswinrt/handling-windows-runtime-events-in-javascript.md)   
 [Representación de JavaScript de tipos de Windows Runtime](../jswinrt/javascript-representation-of-windows-runtime-types.md)   
 [JavaScript Projection of Windows Runtime DateTime and TimeSpan](../jswinrt/windows-runtime-datetime-and-timespan-representations.md) (Proyección de JavaScript de DateTime y TimeSpan de Windows Runtime)
