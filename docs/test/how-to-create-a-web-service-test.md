---
title: Crear una prueba de servicio web en Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, creating Web service tests
- Web services [Visual Studio ALM], creating
- service tests, Web
ms.assetid: fbcd57ee-06ad-4260-8694-09f8e0f93e39
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: de90977a239bf728de3fa98978fd134a014200db
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/20/2018
ms.locfileid: "39180079"
---
# <a name="how-to-create-a-web-service-test"></a>Cómo: Crear una prueba de servicios Web

Para probar servicios web, puede utilizar una prueba de rendimiento web. Las opciones **Insertar solicitud** e **Insertar solicitud de servicio web** permiten personalizar las solicitudes individuales del **Editor de pruebas de rendimiento web** para buscar páginas de servicios web. Normalmente, estas páginas no se muestran en la aplicación web. Por consiguiente, debe personalizar la solicitud para obtener acceso a estas páginas.

Los procedimientos que se muestran a continuación utilizan un servicio web que está incluido dentro del Commerce Starter Kit. Puede descargarlo desde [ASP.NET Commerce Starter Kit](http://go.microsoft.com/fwlink/?LinkId=181469).

 **Requisitos**

-   Visual Studio Enterprise

## <a name="to-test-a-web-service"></a>Para probar un servicio Web

1.  Cree una nueva prueba de rendimiento web. En cuanto se abra el explorador, elija **Detener**.

2.  En el **Editor de pruebas de rendimiento web**, haga clic con el botón derecho en la prueba de rendimiento web y seleccione **Agregar solicitud de servicio web**.

3.  En la propiedad **Url** de la nueva solicitud, escriba el nombre del servicio web, por ejemplo, **http://localhost/storecsvs/InstantOrder.asmx**.

4.  Abra una sesión independiente del explorador y escriba la dirección URL de la página .asmx en la barra de herramientas **Dirección**. Seleccione el método que desee probar y examine el mensaje SOAP. Contiene una `SOAPAction`.

5.  En el **Editor de pruebas de rendimiento web**, haga clic con el botón derecho en la solicitud y seleccione **Agregar encabezado** para agregar un nuevo encabezado. En la propiedad **Nombre**, escriba `SOAPAction`. En la propiedad **Valor**, escriba el valor que vea en `SOAPAction`, por ejemplo, `"http://tempuri.org/CheckStatus"`.

6.  Expanda el nodo URL en el editor, elija el nodo **Texto de la cadena** y, en la propiedad **Tipo de contenido**, escriba el valor `text/xml`.

7.  Vuelva al explorador del paso 4, seleccione la parte XML de la solicitud SOAP desde la página de descripción del servicio web y cópiela en el Portapapeles.

8.  El contenido XML presenta un aspecto similar al del siguiente ejemplo:

     ```xml
     <?xml version="1.0" encoding="utf-8"?>
     <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
     <soap:Body>
       <CheckStatus xmlns="http://tempuri.org/">
         <userName>string</userName>
         <password>string</password>
         <orderID>int</orderID>
       </CheckStatus>
     </soap:Body>
     </soap:Envelope>
     ```

9. Vuelva al **Editor de pruebas de rendimiento web** y, luego, elija los puntos suspensivos (…) en la propiedad **Texto de la cadena**. Pegue el contenido del Portapapeles en la propiedad.

10. Debe reemplazar cualquier valor de marcador de posición del contenido XML por valores válidos para que la prueba se supere. En el ejemplo anterior, reemplazaría las dos instancias de `string` y un `int`. Esta operación del servicio web sólo finaliza si hay un usuario registrado que ha hecho un pedido.

11. Haga clic con el botón derecho en la solicitud de servicio web y seleccione **Agregar parámetro QueryString de dirección URL**.

12. Asigne un nombre y un valor al parámetro de cadena de consulta. En el ejemplo anterior, el nombre es `op` y el valor es `CheckStatus`. Esta información identifica la operación del servicio web que se va a realizar.

    > [!NOTE]
    > Puede usar enlaces de datos en el cuerpo SOAP para reemplazar cualquier valor de marcador de posición por valores enlazados a datos mediante la sintaxis `{{DataSourceName.TableName.ColumnName}}`.

13. Ejecute la prueba. En el panel superior del **Visor de resultados de pruebas de rendimiento web**, seleccione la solicitud de servicio web. En el panel inferior, seleccione la pestaña Explorador web. Se mostrará el XML devuelto por el servicio web, así como los resultados de cualquier operación realizada.

## <a name="see-also"></a>Vea también

- [Crear código y complementos personalizados para las pruebas de carga](../test/create-custom-code-and-plug-ins-for-load-tests.md)