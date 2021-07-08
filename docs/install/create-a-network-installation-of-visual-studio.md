---
title: Creación de una instalación basada en red
description: Obtenga información sobre cómo crear un punto de instalación de red para la implementación de Visual Studio dentro de una empresa.
ms.date: 04/06/2021
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 4CABFD20-962E-482C-8A76-E4012052F701
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 080c4450cfcdca28386811865229af75303beb6a
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307536"
---
# <a name="create-a-network-installation-of-visual-studio"></a>Creación de una instalación de red de Visual Studio

A veces, un administrador de empresa quiere crear un punto de instalación de red que contenga los archivos de Visual Studio que se pueden implementar en las estaciones de trabajo cliente. Esto se hace para facilitar escenarios en los que las máquinas del cliente pueden tener permisos limitados o acceso limitado a internet, o cuando los equipos internos quieren realizar pruebas de compatibilidad antes de que su organización decida usar de forma estándar una versión determinada del conjunto de herramientas para desarrolladores. Hemos diseñado Visual Studio para que un administrador pueda _crear un diseño de red_ que, básicamente, cree una caché de archivos ubicada en un recurso compartido de red estático interno que incluye todos los archivos de Visual Studio para la instalación inicial y todas las actualizaciones futuras del producto.

 > [!NOTE]
 >  - Si tiene varias ediciones de Visual Studio en uso dentro de su empresa como, por ejemplo, Visual Studio 2019 Professional y Visual Studio 2019 Enterprise, debe crear un recurso compartido de instalación de red aparte para cada edición.
 >  - Le recomendamos que decida cómo quiere que los clientes reciban las actualizaciones del producto _antes_ de realizar la instalación inicial del cliente.  Esto hace que sea más fácil asegurarse de que las opciones de configuración se establezcan correctamente. Entre las opciones se incluye la posibilidad de que los clientes obtengan actualizaciones de la ubicación de diseño de red o de Internet. 
 >  - El diseño original de la instalación de Visual Studio y todas las actualizaciones de productos posteriores deben encontrarse en el mismo directorio de red para asegurarse de que la funcionalidad de reparación y desinstalación funciona correctamente.

## <a name="download-the-visual-studio-bootstrapper"></a>Descarga del programa previo de Visual Studio

Descargue el archivo de programa previo correspondiente a la edición de Visual Studio que quiera. Asegúrese de seleccionar **Guardar** y, después, **Abrir carpeta**.

::: moniker range="vs-2017"

Para obtener la versión más reciente del programa previo para la versión 15.9 de Visual Studio 2017, vaya a la página [Versiones anteriores de Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/) y descargue uno de los siguientes archivos de arranque:

| Edición                                      | Filename            |
|----------------------------------------------|---------------------|
| Visual Studio 2017 Enterprise versión 15.9   | vs_enterprise.exe   |
| Visual Studio 2017 Professional versión 15.9 | vs_professional.exe |
| Visual Studio 2017 Build Tools versión 15.9  | vs_buildtools.exe   |

Otros programas previos admitidos incluyen vs_feedbackclient.exe, vs_teamexplorer.exe, vs_testagent.exe, vs_testcontroller.exe y vs_testprofessional.exe.

::: moniker-end

::: moniker range="vs-2019"

Para empezar, descargue el programa previo de Visual Studio 2019 desde la [Página de descargas de Visual Studio](https://visualstudio.microsoft.com/downloads) o desde la página de [Versiones de Visual Studio 2019](/visualstudio/releases/2019/history#installing-an-earlier-release) para la versión y edición elegidas de Visual Studio.  El archivo ejecutable (o, para ser más específicos, un archivo de programa previo) coincidirá o será similar a uno de los siguientes:

| Edición                    | Descargar                                                                                                                                                                                                                           |
|----------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Visual Studio Enterprise   | [vs_enterprise.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2019)     |
| Visual Studio Professional | [vs_professional.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2019) |
| Visual Studio Build Tools  | [vs_buildtools.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=buildtools&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019)     |

Otros programas previos admitidos incluyen [vs_teamexplorer.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/4026077127d25d33789f3882998266946608d8ada378b6ed7c8fff8c07f3dde2/vs_TeamExplorer.exe), [vs_testagent.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/1383bf8bcda3d0e986a2e42c14114aaea8a7b085d31aa0623c9f70b2bad130e4/vs_TestAgent.exe) y [vs_testcontroller.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/54dcf24b76e7cd9fb8be0ac518a9dfba6daf18fe9b2aa1543411b1cda8820918/vs_TestController.exe).

::: moniker-end

::: moniker range=">=vs-2022"

>![!TIP]
> Todavía no hay versiones publicadas de Visual Studio 2022 disponibles; los programas previos siguientes son para la versión preliminar de Visual Studio 2022.
Para empezar, descargue el programa previo de Visual Studio 2022 de la [página de descargas de Visual Studio](https://aka.ms/vs2022preview).

| Edición                    | Descargar                                                                             |
|----------------------------|--------------------------------------------------------------------------------------|
| Visual Studio Enterprise   | [vs_enterprise.exe](https://aka.ms/vs/17/preview/bootstrapper/vs_enterprise.exe)     |
| Visual Studio Professional | [vs_professional.exe](https://aka.ms/vs/17/preview/bootstrapper/vs_professional.exe) |

::: moniker-end

::: moniker range="vs-2017"

>[!TIP]
>Si previamente descargó un archivo de programa previo y quiere comprobar su versión, aquí se muestra cómo hacerlo. En Windows, abra el Explorador de archivos, haga clic con el botón derecho en el archivo de programa previo, elija **Propiedades**, seleccione la pestaña **Detalles** y, luego, fíjese en el número de **versión del producto**. Para hacer coincidir ese número con una versión de Visual Studio, consulte la página [Números de compilación y fechas de lanzamiento de Visual Studio](visual-studio-build-numbers-and-release-dates.md).

::: moniker-end

::: moniker range="vs-2019"

>[!TIP]
>Si previamente descargó un archivo de programa previo y quiere comprobar su versión, aquí se muestra cómo hacerlo. En Windows, abra el Explorador de archivos, haga clic con el botón derecho en el archivo de programa previo, elija **Propiedades**, seleccione la pestaña **Detalles** y, luego, fíjese en el número de **versión del producto**. Para hacer coincidir ese número con una versión de Visual Studio, consulte la página [Versiones de Visual Studio 2019](/visualstudio/releases/2019/history).

::: moniker-end

::: moniker range=">=vs-2022"

>[!TIP]
>Si previamente descargó un archivo de programa previo y quiere comprobar su versión, aquí se muestra cómo hacerlo. En Windows, abra el Explorador de archivos, haga clic con el botón derecho en el archivo de programa previo, elija **Propiedades**, seleccione la pestaña **Detalles** y, luego, fíjese en el número de **versión del producto**. Para hacer coincidir ese número con una versión de Visual Studio, vea [Versiones de Visual Studio 2022](/visualstudio/releases/2022/history).

::: moniker-end

## <a name="create-an-offline-installation-folder"></a>Creación de una carpeta de instalación sin conexión

Deberá disponer de conexión a Internet para poder completar este paso.

Abra un símbolo del sistema, desplácese hasta el directorio en el que descargó el programa previo y use los parámetros del programa previo tal y como se define en la página [Usar parámetros de la línea de comandos para instalar Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) para crear y mantener la caché de instalación de red. A continuación se muestran algunos ejemplos comunes de la creación de diseños iniciales y en [Ejemplos de parámetros de la línea de comandos para la instalación de Visual Studio](../install/command-line-parameter-examples.md).  

   > [!IMPORTANT]
   > Un diseño completo inicial para una configuración regional de un solo idioma requiere aproximadamente 35 GB de espacio en disco para Visual Studio Community y 42 GB para Visual Studio Enterprise. Las [configuraciones regionales de idiomas](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales) adicionales requieren aproximadamente 0,5 GB cada una. Vea la sección [Personalización del diseño de red](#customize-the-network-layout) para obtener más información. Tenga en cuenta que las actualizaciones de diseño posteriores también deben almacenarse en esta misma ubicación de red, por lo que se espera que el contenido del directorio de la ubicación de diseño de red sea bastante grande con el tiempo.  

- Para crear un diseño inicial de Visual Studio Enterprise con todos los lenguajes y todas las características, ejecute:

  ```vs_enterprise.exe --layout c:\VSLayout```

- Para crear un diseño inicial de Visual Studio Professional con todos los lenguajes y todas las características, ejecute:

  ```vs_professional.exe --layout c:\VSLayout```

## <a name="modify-the-responsejson-file"></a>Modificación del archivo response.json

Puede modificar el archivo `response.json` para establecer valores predeterminados que se usan cuando se ejecuta el programa de instalación.  Por ejemplo, puede configurar el archivo `response.json` para elegir un conjunto específico de cargas de trabajo que se deberían seleccionar automáticamente. También puede configurar `response.json` para especificar si el cliente solo debe recibir los archivos actualizados de la ubicación de diseño de red. Consulte [Automatización de la instalación de Visual Studio con un archivo de respuesta](../install/automated-installation-with-response-file.md) para más información. 

Si surge un problema con el programa previo de Visual Studio que genera un error al emparejarlo con un archivo `response.json`, vea la página [Solución de problemas de errores relacionados con la red al instalar o usar Visual Studio](../install/troubleshooting-network-related-errors-in-visual-studio.md#error-failed-to-parse-id-from-parent-process) para obtener más información.

## <a name="copy-the-layout-to-a-network-share"></a>Copia del diseño en un recurso compartido de red

Hospede el diseño en un recurso compartido de red para que se pueda ejecutar desde las máquinas del cliente.

En el ejemplo siguiente se usa [`xcopy`](/windows-server/administration/windows-commands/xcopy/). Si quiere, también puede usar [`robocopy`](/windows-server/administration/windows-commands/robocopy/).

::: moniker range="vs-2017"

Ejemplo:

```shell
xcopy /e c:\VSLayout \\server\products\VS2017
```

::: moniker-end

::: moniker range="vs-2019"

```shell
xcopy /e c:\VSLayout \\server\products\VS2019
```

::: moniker-end

::: moniker range=">=vs-2022"

```shell
xcopy /e c:\VSLayout \\server\products\VS2022
```

::: moniker-end

> [!IMPORTANT]
> Para evitar errores, asegúrese de que la ruta de acceso completa del diseño tenga menos de 80 caracteres.

## <a name="customize-the-network-layout"></a>Personalización del diseño de red

Existen varias opciones que puede usar para personalizar el diseño de red. Puede crear un diseño parcial que solo contenga un conjunto específico de [configuraciones regionales de idioma](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales), [cargas de trabajo y componentes, y sus dependencias recomendados u opcionales](workload-and-component-ids.md). Esta opción puede resultar útil si sabe que solo va a implementar un subconjunto de las cargas de trabajo en las estaciones de trabajo cliente. Entre los parámetros de línea de comandos comunes para personalizar el diseño se incluyen:

* `--add` para especificar [identificadores de carga de trabajo o componente](workload-and-component-ids.md). <br>Si se usa `--add`, solo se descargan esas cargas de trabajo y componentes especificados con `--add`.  Si no se usa `--add`, se descargan todos los componentes y cargas de trabajo.
* `--includeRecommended` para incluir todos los componentes recomendados para los identificadores de carga especificados.
* `--includeOptional` para incluir todos los componentes recomendados y opcionales para los identificadores de carga de trabajo especificados.
* `--lang` para especificar [configuraciones regionales de idioma](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales).

Estos son algunos ejemplos de cómo crear un diseño parcial personalizado.

* Para descargar todas las cargas de trabajo y los componentes para un solo idioma, ejecute:

    ```shell
    vs_enterprise.exe --layout C:\VSLayout --lang en-US
    ```

* Para descargar todas las cargas de trabajo y los componentes para varios idiomas, ejecute:

    ```shell
    vs_enterprise.exe --layout C:\VSLayout --lang en-US de-DE ja-JP
    ```

* Para descargar una carga de trabajo para todos los idiomas, ejecute:

    ```shell
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --includeRecommended
    ```

* Para descargar dos cargas de trabajo y un componente opcional para tres idiomas, ejecute:

    ```shell
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended --lang en-US de-DE ja-JP
    ```

* Para descargar dos cargas de trabajo y todos sus componentes recomendados:

    ```shell
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended
    ```

* Para descargar dos cargas de trabajo y todos sus componentes recomendados y opcionales, ejecute:

    ```shell
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeOptional
    ```

### <a name="save-your-layout-options"></a>Guardado de las opciones de diseño

Cuando ejecuta un comando de diseño, las opciones que especifique se guardan, como las cargas de trabajo y los idiomas. Los comandos de diseño posteriores incluirán todas las opciones anteriores.  Aquí se muestra un ejemplo de un diseño con una carga de trabajo solo para inglés:

```shell
vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US
```

Si quiere actualizar ese diseño a una versión más reciente, no tiene que especificar ningún parámetro de línea de comandos adicional. Las opciones anteriores se guardan y se usan mediante cualquier comando de diseño posterior en esta carpeta de diseño.  El comando siguiente actualizará el diseño parcial existente.

```shell
vs_enterprise.exe --layout c:\VSLayout
```

Si quiere agregar una carga de trabajo adicional, aquí se muestra un ejemplo de cómo realizarlo. En este caso, agregaremos la carga de trabajo de Azure y un idioma localizado.  Ahora tanto el escritorio administrado como Azure se incluyen en este diseño.  Los recursos de idioma para inglés y alemán se incluyen para todas estas cargas de trabajo. El diseño se actualiza a la última versión disponible.

```shell
vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --lang de-DE
```

Si quiere actualizar un diseño existente en un diseño completo, use la opción --all, como se muestra en el ejemplo siguiente.

```shell
vs_enterprise.exe --layout c:\VSLayout --all
```

## <a name="deploy-from-a-network-installation"></a>Implementación de una instalación de red

Los administradores pueden implementar Visual Studio en estaciones de trabajo cliente como parte de un script de instalación. O bien, los usuarios que tienen derechos de administrador pueden ejecutar la instalación directamente desde el recurso compartido para instalar Visual Studio en sus máquinas.

* Para realizar la instalación, los usuarios pueden ejecutar el comando siguiente: <br>

    ```shell
    \\server\products\VS\vs_enterprise.exe
    ```

* Los administradores pueden realizar la instalación en modo desatendido con la ejecución del comando siguiente:

    ```shell
    \\server\products\VS\vs_enterprise.exe --quiet --wait --norestart
    ```

> [!IMPORTANT]
> Para evitar errores, asegúrese de que la ruta de acceso completa del diseño tenga menos de 80 caracteres.

> [!TIP]
> Cuando se ejecuta como parte de un archivo por lotes, la opción `--wait` garantiza que el proceso `vs_enterprise.exe` espere hasta que la instalación haya finalizado antes de devolver un código de salida.
>
> Resulta muy útil si un administrador de empresa quiere realizar más acciones en una instalación completada (por ejemplo, para [aplicar una clave de producto a una instalación correcta](automatically-apply-product-keys-when-deploying-visual-studio.md)), pero debe esperar a que la instalación finalice para controlar el código de retorno desde esa instalación.
>
> Si no usa `--wait`, el proceso `vs_enterprise.exe` se cierra antes de que la instalación se complete y devuelve un código de salida incorrecto que no representa el estado de la operación de instalación.
>

::: moniker range=">=vs-2019"
> [!IMPORTANT]
> En el caso de las instalaciones sin conexión, si recibe un mensaje de error que indica que no se encuentra un producto que coincida con los parámetros especificados, asegúrese de que está usando el modificador `--noweb` con la versión 16.3.5 o posterior.
>
::: moniker-end

Cuando realice la instalación desde un diseño, el contenido que está instalado se adquirirá del diseño. Sin embargo, si selecciona un componente que no está en el diseño, se obtendrá de Internet.  Si quiere evitar que la instalación de Visual Studio descargue cualquier contenido que no esté en su diseño, use la opción `--noWeb`. Si se usa `--noWeb` y al diseño le falta cualquier contenido seleccionado que se va a instalar, se produce un error en la instalación.

> [!TIP]
> Si quiere instalar desde un origen sin conexión en un equipo que no está conectado a Internet, especifique las opciones `--noWeb` y `--noUpdateInstaller`. La primera evita la descarga de cargas de trabajo actualizadas, componentes, etc. La segunda impide que el instalador se actualice automáticamente desde la web.

> [!IMPORTANT]
> La opción `--noWeb` no impide que la configuración de Visual Studio en un equipo conectado a Internet busque actualizaciones. Para más información, consulte la página [Control de actualizaciones a implementaciones de Visual Studio basadas en red](controlling-updates-to-visual-studio-deployments.md).

### <a name="error-codes"></a>Códigos de error

Si ha usado el parámetro `--wait`, la variable de entorno `%ERRORLEVEL%` se establece en uno de los siguientes valores, según el resultado de la operación:

[!INCLUDE[install-error-codes-md](includes/install-error-codes-md.md)]

## <a name="update-a-network-install-layout"></a>Actualización de un diseño de instalación de red

A medida que estén disponibles actualizaciones de productos, puede que quiera [actualizar el diseño de instalación de red](update-a-network-installation-of-visual-studio.md) para incorporar paquetes actualizados.

## <a name="how-to-create-a-layout-for-a-previous-visual-studio-release"></a>Creación de un diseño para una versión anterior de Visual Studio

En primer lugar, debe saber que hay dos tipos de programas previos de Visual Studio: uno que se puede caracterizar por las palabras "última", "actual", "perenne" y "sugerencia", y otra que básicamente significa "versión corregida". Ambos tipos de archivos de programa previo tienen el mismo nombre exacto y la mejor manera de distinguir el tipo es prestar atención al lugar desde el que se descargó. Los programas previos de Visual Studio disponibles en la [Página de descargas de Visual Studio](https://visualstudio.microsoft.com/downloads) se consideran programas previos perennes de Visual Studio y siempre instalan o actualizan la versión más reciente que está disponible en el canal en el momento en que se ejecuta el programa previo. Los programas previos de Visual Studio disponibles en las páginas de [Versiones de Visual Studio 2019](/visualstudio/releases/2019/history) o [Versiones de Visual Studio 2022](/visualstudio/releases/2022/history), o que están insertados en la actualización de administrador en el catálogo de Microsoft Update, instalan una versión fija determinada del producto.

Por tanto, si descarga hoy un programa previo perenne de Visual Studio y lo ejecuta de aquí a seis meses, se instalará la versión de Visual Studio que esté disponible en el momento que se ejecute el programa previo. Está diseñado para instalar siempre los bits más recientes y mantenerlo actualizado.

Si descarga un programa previo de vínculo fijo o ejecuta una actualización de administrador que descargó del Catálogo de Microsoft, siempre instalará una versión determinada del producto, independientemente de cuándo se haya ejecutado.

Por último, puede crear un diseño de red con cualquiera de estos programas previos, y la versión que se creará en el diseño dependerá del programa previo que esté usando; por ejemplo, será una versión fija o actual. Después, puede actualizar el diseño de red con cualquier programa previo posterior o también puede usar el paquete de actualización de administrador del Catálogo de Microsoft Update. Independientemente de cómo realice la actualización, el diseño actualizado resultante será una memoria caché de paquetes que contenga una versión determinada del producto y se comportará como un programa previo de vínculo fijo. Por lo tanto, cada vez que el cliente instale desde el diseño, se instalará la versión específica de Visual Studio existente en ese diseño, aunque puede existir una versión más reciente en línea.

### <a name="how-to-get-support-for-your-offline-installer"></a>Obtención de soporte técnico para el instalador sin conexión

Si experimenta un problema con la instalación sin conexión, queremos saberlo. La mejor manera para hacérnoslo saber es usar la herramienta [Notificar un problema](../ide/how-to-report-a-problem-with-visual-studio.md). Con esta herramienta puede enviarnos la telemetría y los registros que necesitamos para ayudarnos a diagnosticar y corregir el problema.

También ofrecemos una opción de soporte técnico de [**chat de instalación**](https://visualstudio.microsoft.com/vs/support/#talktous) para incidencias relacionadas con la instalación (solo en inglés).

Tenemos también otras opciones de soporte técnico disponibles. Para obtener una lista, consulte nuestra página [Comentarios](../ide/feedback-options.md).

## <a name="see-also"></a>Vea también

- [Guía del administrador de Visual Studio](visual-studio-administrator-guide.md)
- [Actualizar una instalación basada en red de Visual Studio](update-a-network-installation-of-visual-studio.md)
- [Solución de problemas de errores relacionados con la red al instalar o usar Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md)
- [Control updates to network-based Visual Studio deployments](controlling-updates-to-visual-studio-deployments.md) (Control de actualizaciones de implementaciones de Visual Studio basadas en red)
- [Ciclo de vida y mantenimiento del producto de Visual Studio](/visualstudio/releases/2019/servicing/)
- [Actualización de Visual Studio mientras se encuentra en una base de referencia de mantenimiento](update-servicing-baseline.md)
- [Usar parámetros de la línea de comandos para instalar Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
- [Identificadores de cargas de trabajo y componentes de Visual Studio](workload-and-component-ids.md)
- [Instalar los certificados necesarios para la instalación sin conexión de Visual Studio](install-certificates-for-visual-studio-offline.md)
