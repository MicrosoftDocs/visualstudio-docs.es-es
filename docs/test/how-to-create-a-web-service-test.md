---
title: Creación de una prueba de servicios web
ms.date: 06/30/2020
ms.topic: how-to
helpviewer_keywords:
- Web performance tests, creating Web service tests
- Web services [Visual Studio ALM], creating
- service tests, Web
ms.assetid: fbcd57ee-06ad-4260-8694-09f8e0f93e39
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9934f48e6d5900a418995eb96d357b4ea1ea532f
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "85814764"
---
# <a name="how-to-create-a-web-service-test"></a>Procedimiento Crear una prueba de servicios web

Para probar servicios web, puede utilizar una prueba de rendimiento web. Las opciones **Insertar solicitud** e **Insertar solicitud de servicio web** permiten personalizar las solicitudes individuales del **Editor de pruebas de rendimiento web** para buscar páginas de servicios web. Normalmente, estas páginas no se muestran en la aplicación web. Por consiguiente, debe personalizar la solicitud para obtener acceso a estas páginas.

>[!NOTE]
> La funcionalidad de pruebas de carga y rendimiento web está en desuso en Visual Studio 2019. Para Application Insights, las pruebas web de varios pasos dependen de los archivos de pruebas web de Visual Studio. Se [anunció](https://devblogs.microsoft.com/devops/cloud-based-load-testing-service-eol/) que Visual Studio 2019 será la última versión con la funcionalidad de prueba web. Es importante comprender que, aunque no se agregarán nuevas características, la funcionalidad de pruebas web de Visual Studio 2019 todavía se admite y se seguirá admitiendo durante el ciclo de vida de soporte técnico del producto. El equipo de productos de Azure Monitor ha abordado las preguntas sobre el futuro de las pruebas de disponibilidad de varios pasos [aquí](https://github.com/MicrosoftDocs/azure-docs/issues/26050#issuecomment-468814101).

**Requisitos**

Visual Studio Enterprise

## <a name="to-create-a-simple-web-service"></a>Creación de un servicio web simple

Para realizar pruebas, puede usar su propio servicio web o la plantilla de servicio web básica (ASMX) incluida en Visual Studio. Para crear un servicio web simple mediante esta plantilla:

1. En Visual Studio, cree un proyecto con la plantilla de aplicación web de ASP.NET (.NET Framework) y seleccione la plantilla **vacía** cuando se le solicite. Escriba un nombre y cree el proyecto.

1. En el Explorador de soluciones, haga clic con el botón derecho en el nodo del proyecto, elija **Agregar** > **Nuevo elemento** y, después, **Servicio web (ASMX)** . Agregue el servicio web.

1. Abra *WebService1.asmx* y reemplace el método web predeterminado `HelloWorld` por el código siguiente.

   ```csharp
   public string HelloWorld(string str)
   {
      return "Hello, " + str;
   }
   ```

## <a name="install-the-load-testing-component"></a>Instalar el componente de prueba de carga

Si aún no tiene instalado el componente de herramientas de pruebas de carga y rendimiento web, deberá instalarlo con el Instalador de Visual Studio.

1. Abra el **Instalador de Visual Studio** desde el menú **Iniciar** de Windows. También puede tener acceso a él en Visual Studio desde el cuadro de diálogo de nuevo proyecto, o bien seleccionando **Herramientas** > **Get Tools and Features** (Obtener herramientas y características) en la barra de menús.

1. En el **Instalador de Visual Studio**, elija la pestaña **Componentes individuales** y desplácese hacia abajo hasta la sección **Depuración y pruebas**. Seleccione **Herramientas de rendimiento web y pruebas de carga**.

   ![Componente de herramientas de rendimiento web y pruebas de carga](media/web-perf-load-testing-tools-component.png)

1. Elija el botón **Modificar**.

   El componente de herramientas de rendimiento web y pruebas de carga se instala.

## <a name="create-a-web-test-project"></a>Creación de un proyecto de prueba web

Una prueba web requiere la plantilla Proyecto de prueba de carga y rendimiento web. En esta sección, vamos a crear un proyecto de prueba de carga de C#. También puede crear un proyecto de prueba de carga de Visual Basic, si lo prefiere.

::: moniker range="vs-2017"

1. Abra Visual Studio.

   Si usa la plantilla de servicio web de ejemplo (ASMX), puede agregar el proyecto de prueba web a la misma solución.

2. En la barra de menús, seleccione **Archivo** > **Nuevo** > **Proyecto**.

   Aparece el cuadro de diálogo **Nuevo proyecto** .

3. En el cuadro de diálogo **Nuevo proyecto**, expanda **Instalado** y **Visual C#** y, después, elija la categoría **Prueba**. Elija la plantilla **Proyecto de prueba de carga y rendimiento web**.

   ![Plantilla de proyecto de prueba de carga y rendimiento web](media/web-perf-load-test-project-template.png)

4. Escriba un nombre para el proyecto si no quiere usar el predeterminado y elija **Aceptar**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Abra Visual Studio.

   Si usa la plantilla de servicio web de ejemplo (ASMX), puede agregar el proyecto de prueba web a la misma solución.

2. En la ventana de inicio, elija **Crear un proyecto nuevo**.

3. En el cuadro de búsqueda de la página **Crear un proyecto**, escriba **prueba web** y seleccione la plantilla **Proyecto de prueba de carga y rendimiento web\[En desuso]** para C#. Seleccione **Siguiente**.

4. Escriba un nombre para el proyecto si no quiere usar el predeterminado y elija **Crear**.

::: moniker-end

   Visual Studio crea el proyecto y muestra los archivos en el **Explorador de soluciones**. Inicialmente, el proyecto contiene un archivo de prueba web denominado *WebTest1.webtest*.

## <a name="to-test-a-web-service"></a>Para probar un servicio web

1. Inicie el servicio web y, si es necesario, elija **Detener** para pausar el servicio.

1. En el proyecto de prueba web, abra *WebTest1.webtest*, que iniciará el Editor de pruebas de rendimiento web. En el editor de pruebas, haga clic con el botón derecho en la prueba de rendimiento web y seleccione **Agregar solicitud de servicio web**.

1. En la propiedad **Url** de la nueva solicitud, escriba el nombre del servicio web, por ejemplo, **https://localhost:44318/WebService1.asmx** .

1. Para el servicio web, abra una sesión independiente del explorador y escriba la dirección URL de la página *.asmx* en la barra de herramientas **Dirección**. En la parte superior de la página web, seleccione el método que quiera probar y examine el mensaje SOAP. (En el servicio web de ejemplo, el método es HelloWorld). Cuando abra el método, verá que contiene un elemento `SOAPAction`.

1. En el **Editor de pruebas de rendimiento web**, haga clic con el botón derecho en la solicitud y seleccione **Agregar encabezado** para agregar un nuevo encabezado. En la propiedad **Nombre**, escriba `SOAPAction`. En la propiedad **Valor**, escriba el valor que vea en `SOAPAction`; por ejemplo, *http://tempuri.org/HelloWorld* .

1. Expanda el nodo URL en el editor de prueba, elija el nodo **Texto de la cadena** y, en la propiedad **Tipo de contenido**, escriba el valor `text/xml`.

1. Vuelva al explorador del paso 4, seleccione la parte XML de la solicitud SOAP desde la página de descripción del servicio web y cópiela en el Portapapeles.

   El contenido XML presenta un aspecto similar al del siguiente ejemplo:

     ```xml
     <?xml version="1.0" encoding="utf-8"?>
     <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
       <soap:Body>
         <HelloWorld xmlns="http://tempuri.org/">
           <str>string</str>
         </HelloWorld>
       </soap:Body>
     </soap:Envelope>
     ```

1. Vuelva al Editor de pruebas de rendimiento web y haga clic en los puntos suspensivos **(…)** en la propiedad **Texto de la cadena**. Pegue el contenido del Portapapeles en la propiedad.

1. Reemplace cualquier valor de marcador de posición del contenido XML por valores válidos para que la prueba se supere. En el ejemplo anterior, reemplazaría la instancia de `string` por un nombre.

1. Haga clic con el botón derecho en la solicitud de servicio web y seleccione **Agregar parámetro QueryString de dirección URL**.

1. Asigne un nombre y un valor al parámetro de cadena de consulta. En el ejemplo anterior, el nombre es `op` y el valor es `HelloWorld`. Esta información identifica la operación del servicio web que se va a realizar.

    > [!NOTE]
    > Puede usar enlaces de datos en el cuerpo SOAP para reemplazar cualquier valor de marcador de posición por valores enlazados a datos mediante la sintaxis `{{DataSourceName.TableName.ColumnName}}`.

1. Ejecute la prueba. En el panel superior del **Visor de resultados de pruebas de rendimiento web**, seleccione la solicitud de servicio web. En el panel inferior, seleccione la pestaña **Explorador web**. Se mostrará el XML devuelto por el servicio web, así como los resultados de cualquier operación realizada.

   Busque los resultados de su solicitud de servicio web.

## <a name="see-also"></a>Vea también

- [Crear código y complementos personalizados para las pruebas de carga](../test/create-custom-code-and-plug-ins-for-load-tests.md)
