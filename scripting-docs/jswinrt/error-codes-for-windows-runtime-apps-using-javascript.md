---
title: "Códigos de error para aplicaciones de Windows Runtime mediante JavaScript | Microsoft Docs"
ms.custom: 
ms.date: 05/10/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- JavaScript, Windows Runtime error codes
- VS.WebClient.Help.APPHOST9601
- VS.WebClient.Help.APPHOST9602
- VS.WebClient.Help.APPHOST9603
- VS.WebClient.Help.APPHOST9604
- VS.WebClient.Help.APPHOST9605
- VS.WebClient.Help.APPHOST9606
- VS.WebClient.Help.APPHOST9607
- VS.WebClient.Help.APPHOST9608
- VS.WebClient.Help.APPHOST9610
- VS.WebClient.Help.APPHOST9611
- VS.WebClient.Help.APPHOST9613
- VS.WebClient.Help.APPHOST9614
- VS.WebClient.Help.APPHOST9615
- VS.WebClient.Help.APPHOST9616
- VS.WebClient.Help.APPHOST9617
- VS.WebClient.Help.APPHOST9618
- VS.WebClient.Help.APPHOST9619
- VS.WebClient.Help.APPHOST9620
- VS.WebClient.Help.APPHOST9623
- VS.WebClient.Help.APPHOST9624
- VS.WebClient.Help.APPHOST9626
ms.assetid: 4c6d4e90-602a-4b56-ae74-3458929da442
caps.latest.revision: 1
author: erikadoyle
ms.author: edoyle
manager: jken
ms.translationtype: HT
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 89b91a3246d0a6e2980459c2c35c7361168bccd4
ms.contentlocale: es-es
ms.lasthandoff: 08/11/2017

---
# <a name="error-codes-for-windows-runtime-apps-using-javascript"></a>Códigos de error para aplicaciones de Windows Runtime mediante JavaScript
Estos son los códigos de error mostrados por la consola de Microsoft Visual Studio al desarrollar aplicaciones de Windows Runtime mediante JavaScript.
  
Error | Comentarios
----- | -------
APPHOST9601: "No se puede cargar *remoteURI*. Una aplicación no puede cargar contenido web remoto en el contexto local". | Para obtener más información sobre lo que se permite en el contexto web, consulte [Características y restricciones por contexto](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465373.aspx).
APPHOST9602: "javascript:" es un valor de atributo no válido y se omitirá. No use URI "javascript:" en el contexto local". | Por motivos de seguridad, no se puede usar URI "javascript:" en el contexto local. Para obtener más información sobre lo que se permite en el contexto local, consulte [Características y restricciones por contexto](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465373.aspx).
APPHOST9603: "No se puede cargar el complemento ActiveX con el identificador de clase *classID*.  Las aplicaciones no pueden cargar controles ActiveX". | Las aplicaciones de Windows Runtime que usan JavaScript no admiten controles Microsoft ActiveX personalizados. Si necesita un control de interfaz de usuario, use un control web estándar, una biblioteca de controles, o cree su propio control personalizado. Si tiene que realizar lógica personalizada, cree en su lugar un objeto de Windows Runtime personalizado. Para obtener información sobre otras diferencias HTML, CSS y JavaScript, consulte [Características y diferencias de HTML, CSS y JavaScript](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465380.aspx).
APPHOST9604: "No se puede navegar a *uri* porque usa una codificación de caracteres no válida.  Una aplicación solo puede navegar a archivos con codificación UTF8". | Todos los archivos HTML, JavaScript y CSS con acceso desde una instancia de Windows Runtime deben estar codificados en el formato de transformación Unicode de 8 bits (UTF-8). Para obtener información sobre otras diferencias HTML, CSS y JavaScript, consulte [Características y diferencias de HTML, CSS y JavaScript](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465380.aspx).
APPHOST9605: "No se puede navegar a *targetURI* desde *sourceURI* porque el URI de destino está en una zona de mayor seguridad. No se puede navegar desde una zona con menor seguridad a una zona con mayor seguridad, a menos que esté navegando a un contexto local desde un URI de contexto web y haya registrado el URI del contexto local con el método MSApp.addPublicLocalApplicationUri". | Para obtener más información, consulte [MSApp.addPublicLocalApplicationUri](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465759.aspx).
APPHOST9606: *uri* no pude cargarse porque usa una conexión HTTP y la etiqueta META ms-https-connections-only está presente. Solamente se permiten las conexiones HTTPS cuando se usa la etiqueta META ms-https-connections-only. Use una conexión HTTPS o, si no necesita una conexión segura, quite la etiqueta META". | Para obtener más información, consulte [Cómo requerir una conexión HTTPS (HTML)](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh452771.aspx).
APPHOST9607: "La aplicación no puede iniciar el URI en *uri* debido a este error: *failureCode*". | Las causas más habituales de este error son un recurso que falta o un archivo no válido.
APPHOST9608: "La aplicación no pudo navegar a la página about:blank debido a este error: *errorCode*". | 
APPHOST9610: "La aplicación detectó un error al prepararse para navegar a una página de error personalizada: *errorCode*". |
APPHOST9611: "La aplicación no pudo navegar a una página de error personalizada debido a este error: *errorCode*". |
APPHOST9613: "La aplicación no pudo navegar a * uri* debido a este error: *errorCode*". | 
APPHOST9614: "Un documento dentro del iframe solicitó el modo de documento *requestedDocMode*, pero el sistema aplica el modo de documento *currentDocMode*. Iframe usará el modo de documento *currentDocMode*". | Para obtener más información acerca de cómo mostrar contenido web remoto, consulte [Cómo vincular a páginas web externas](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh780594.aspx).
APPHOST9615: "La aplicación no puede descargar el archivo en *uri* porque se invocó mediante programación fuera del contexto local". | Se produce cuando el contenido del contexto web intenta descargar un archivo mediante programación.
APPHOST9616: "Este URI no puede usar API de ubicación geográfica.  Las API de ubicación geográfica solo se pueden invocar desde un URI que forme parte del paquete o esté incluido en el elemento ApplicationContentUris del manifiesto". | Para obtener más información sobre lo que se permite en el contexto web, consulte [Características y restricciones por contexto](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465373.aspx).
APPHOST9617: "Este URI no puede usar API de portapapeles.  Las API de portapapeles solo se pueden invocar desde un URI que forme parte del paquete o esté incluido en el elemento ApplicationContentUris del manifiesto". | Para obtener más información sobre lo que se permite en el contexto web, consulte [Características y restricciones por contexto](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465373.aspx).
APPHOST9618: "Este URI no puede usar window.close.  El método window.close solo se puede invocar desde contenido empaquetado con un esquema URI ms-appx". | Para obtener más información sobre lo que se permite en el contexto web, consulte [Características y restricciones por contexto](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465373.aspx).
APPHOST9619: "La aplicación no puede navegar a *uri* porque una página en el contexto web no puede ser el documento de nivel superior de la aplicación. Cargue la página en un iFrame". | No puede navegar en una página de nivel superior a una página web remota, pero la aplicación puede mostrar una página web en un [iframe](https://msdn.microsoft.com/en-us/library/ms535258(v=vs.85).aspx). Para obtener más información acerca de cómo mostrar contenido web remoto, consulte [Cómo vincular a páginas web externas](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh780594.aspx).
APPHOST9620: "Esta aplicación se cerró porque usó una conexión HTTP y el elemento META ms-https-connections-only está presente. Solamente se permiten las conexiones HTTPS cuando se usa la etiqueta META ms-https-connections-only. Use una conexión HTTPS o, si no necesita una conexión segura, quite el elemento META". | Para obtener más información, consulte [Cómo requerir una conexión HTTPS (HTML)](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh452771.aspx).
APPHOST9623: "La aplicación no pudo resolver *url* debido al error: *errorCode*". | Una causa común de este error es un archivo que falta.  
APPHOST9624: "La aplicación no puede usar un script para cargar la dirección URL *url* porque esta dirección URL inicia otra aplicación. Solo se puede iniciar otra aplicación con la interacción directa del usuario". | Las aplicaciones no pueden iniciar directamente otras aplicaciones. El usuario puede iniciar otras aplicaciones cuando la aplicación implementa determinados contratos. Para obtener más información, consulte [Contratos y extensiones de aplicaciones](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh464906.aspx).
APPHOST9626: "Se detectó una referencia directa al archivo de recursos `ms-appx://1d33240b-0b00-40e4-a416-a4750c48787f/ja-jp\images\logo.scale-140.png`. Esta referencia provoca errores cuando se usa fuera del entorno de depuración". | Debido a la ruta de acceso de archivo de `logo.scale-140.png`, este archivo PNG se trata como un recurso localizado, lo que provoca el error de que no se puede hacer referencia directa a los recursos localizados. Consulte [Globalizar la aplicación (HTML)](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465006.aspx) si pretende usar este archivo como recurso de lenguaje. En caso contrario, intente cambiar el nombre del directorio problemático.
  
## <a name="see-also"></a>Vea también  
 [Uso de Windows Runtime en JavaScript](../jswinrt/using-the-windows-runtime-in-javascript.md)
