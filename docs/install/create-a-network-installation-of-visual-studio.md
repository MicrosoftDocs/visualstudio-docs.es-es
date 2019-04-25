---
title: Creación de una instalación basada en red
description: Obtenga información sobre cómo crear un punto de instalación de red para la implementación de Visual Studio dentro de una empresa.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 4CABFD20-962E-482C-8A76-E4012052F701
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 5e499e54a7cf1c5c50a625cfe03482202e3a1f3f
ms.sourcegitcommit: 509fc3a324b7748f96a072d0023572f8a645bffc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58857430"
---
# <a name="create-a-network-installation-of-visual-studio"></a>Creación de una instalación de red de Visual Studio

Normalmente, un administrador de empresa crea un punto de instalación de red para implementar en estaciones de trabajo cliente. Hemos diseñado Visual Studio para permitirle almacenar en caché los archivos de la instalación inicial junto con todas las actualizaciones de producto en una única carpeta. Este proceso también se conoce como la _creación de un diseño_. 

Hemos realizado esto para que las estaciones de trabajo de cliente puedan usar la misma ubicación de red para administrar su instalación incluso si todavía no han actualizado a la última actualización del servicio.

 > [!NOTE]
 > Si tiene varias ediciones de Visual Studio en uso dentro de su empresa (por ejemplo, Visual Studio Professional y Visual Studio Enterprise), debe crear un recurso compartido de instalación de red aparte para cada edición.

## <a name="download-the-visual-studio-bootstrapper"></a>Descarga del programa previo de Visual Studio

Descargue la edición de Visual Studio que desee. Asegúrese de hacer clic en **Guardar** y, a continuación, haga clic en **Abrir carpeta**.

El archivo ejecutable o, para ser más específicos, un archivo de programa previo, debe coincidir con uno de los siguientes.

::: moniker range="vs-2017"

|Edición | Descargar|
|-------------|-----------------------|
|Visual Studio Enterprise | [**vs_enterprise.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=15&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2017) |
|Visual Studio Professional | [**vs_professional.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=15&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2017) |

Otros programas previos admitidos incluyen [vs_buildtools.exe](https://aka.ms/vs/15/release/vs_buildtools.exe), [vs_feedbackclient.exe](https://aka.ms/vs/15/release/vs_feedbackclient.exe), [vs_teamexplorer.exe](https://aka.ms/vs/15/release/vs_teamexplorer.exe), [vs_testagent.exe](https://aka.ms/vs/15/release/vs_testagent.exe), [vs_testcontroller.exe](https://aka.ms/vs/15/release/vs_testcontroller.exe) y [vs_testprofessional.exe](https://aka.ms/vs/15/release/vs_testprofessional.exe).

::: moniker-end

::: moniker range="vs-2019"

|Edición | Descargar|
|-------------|-----------------------|
|Visual Studio Enterprise | [**vs_enterprise.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2019) |
|Visual Studio Professional | [**vs_professional.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2019) |

Otros programas previos admitidos incluyen [vs_buildtools.exe](https://aka.ms/vs/16/release/vs_buildtools.exe), [vs_teamexplorer.exe](https://aka.ms/vs/16/release/vs_teamexplorer.exe), [vs_testagent.exe](https://aka.ms/vs/16/release/vs_testagent.exe) y [vs_testcontroller.exe](https://aka.ms/vs/16/release/vs_testcontroller.exe).

::: moniker-end

## <a name="create-an-offline-installation-folder"></a>Creación de una carpeta de instalación sin conexión

Deberá disponer de conexión a Internet para poder completar este paso. Para crear una instalación sin conexión con todos los lenguajes y todas las características, utilice uno de los comandos de los ejemplos siguientes.

   > [!IMPORTANT]
   > Un diseño completo de Visual Studio requiere como mínimo 35 GB de espacio en disco y puede tardar un poco en descargarse. Consulte la sección [Personalización del diseño de red](#customize-the-network-layout) para detalles sobre cómo crear un diseño únicamente con los componentes que desea instalar.
   >
   > [!TIP]
   > Asegúrese de ejecutar el comando desde el directorio de descarga. Normalmente, es `C:\Users\<username>\Downloads` en un equipo que ejecuta Windows 10.

- Para Visual Studio Enterprise, ejecute:

  ```vs_enterprise.exe --layout c:\vsoffline```

- Para Visual Studio Professional, ejecute:

  ```vs_professional.exe --layout c:\vsoffline```

## <a name="modify-the-responsejson-file"></a>Modificación del archivo response.json

Puede modificar el archivo response.json para establecer valores predeterminados que se usan cuando se ejecuta el programa de instalación.  Por ejemplo, puede configurar el archivo `response.json` para elegir un conjunto específico de cargas de trabajo que se seleccionan automáticamente.
Consulte [Automatización de la instalación de Visual Studio con un archivo de respuesta](automated-installation-with-response-file.md) para más información.

## <a name="copy-the-layout-to-a-network-share"></a>Copia del diseño en un recurso compartido de red

Hospede el diseño en un recurso compartido de red para que se pueda ejecutar desde otras máquinas.

::: moniker range="vs-2017"

Ejemplo:

```cmd
xcopy /e c:\vsoffline \\server\products\VS2017
```

::: moniker-end

::: moniker range="vs-2019"

```cmd
xcopy /e c:\vsoffline \\server\products\VS2019
```

::: moniker-end

> [!IMPORTANT]
> Para evitar errores, asegúrese de que la ruta de acceso completa del diseño tenga menos de 80 caracteres.

## <a name="customize-the-network-layout"></a>Personalización del diseño de red

Existen varias opciones que puede usar para personalizar el diseño de red. Puede crear un diseño parcial que solo contenga un conjunto específico de [configuraciones regionales de idioma](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales), [cargas de trabajo y componentes, y sus dependencias recomendados u opcionales](workload-and-component-ids.md). Esta opción puede resultar útil si sabe que solo va a implementar un subconjunto de las cargas de trabajo en las estaciones de trabajo cliente. Entre los parámetros de línea de comandos comunes para personalizar el diseño se incluyen:

* `--add` para especificar [identificadores de carga de trabajo o componente](workload-and-component-ids.md). <br>Si se usa `--add`, solo se descargan esas cargas de trabajo y componentes especificados con `--add`.  Si no se usa `--add`, se descargan todos los componentes y cargas de trabajo.
* `--includeRecommended` para incluir todos los componentes recomendados para los identificadores de carga de trabajo especificados.
* `--includeOptional` para incluir todos los componentes recomendados y opcionales para los identificadores de carga de trabajo especificados.
* `--lang` para especificar [configuraciones regionales de idioma](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales).

Estos son algunos ejemplos de cómo crear un diseño parcial personalizado.

* Para descargar todas las cargas de trabajo y los componentes para un solo idioma, ejecute:

    ```cmd
    vs_enterprise.exe --layout C:\vsoffline --lang en-US
    ```

* Para descargar todas las cargas de trabajo y los componentes para varios idiomas, ejecute:

    ```cmd
    vs_enterprise.exe --layout C:\vsoffline --lang en-US de-DE ja-JP
    ```

* Para descargar una carga de trabajo para todos los idiomas, ejecute:

    ```cmd
    vs_enterprise.exe --layout C:\vsoffline --add Microsoft.VisualStudio.Workload.Azure --includeRecommended
    ```

* Para descargar dos cargas de trabajo y un componente opcional para tres idiomas, ejecute:

    ```cmd
    vs_enterprise.exe --layout C:\vsoffline --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended --lang en-US de-DE ja-JP
    ```

* Para descargar dos cargas de trabajo y todos sus componentes recomendados:

    ```cmd
    vs_enterprise.exe --layout C:\vsoffline --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended 
    ```

* Para descargar dos cargas de trabajo y todos sus componentes recomendados y opcionales, ejecute:

    ```cmd
    vs_enterprise.exe --layout C:\vsoffline --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeOptional 
    ```
::: moniker range="vs-2017"

### <a name="new-in-version-153"></a>Novedades de la versión 15.3

::: moniker-end

::: moniker range="vs-2019"

### <a name="save-your-layout-options"></a>Guardado de las opciones de diseño

::: moniker-end

Cuando ejecuta un comando de diseño, las opciones que especifique se guardan, como las cargas de trabajo y los idiomas. Los comandos de diseño posteriores incluirán todas las opciones anteriores.  Aquí se muestra un ejemplo de un diseño con una carga de trabajo solo para inglés:

```cmd
vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US
```

Si quiere actualizar ese diseño a una versión más reciente, no tiene que especificar ningún parámetro de línea de comandos adicional. Las opciones anteriores se guardan y se usan mediante cualquier comando de diseño posterior en esta carpeta de diseño.  El comando siguiente actualizará el diseño parcial existente.

```cmd
vs_enterprise.exe --layout c:\VSLayout
```

Si quiere agregar una carga de trabajo adicional, aquí se muestra un ejemplo de cómo realizarlo. En este caso, agregaremos la carga de trabajo de Azure y un idioma localizado.  Ahora tanto el escritorio administrado como Azure se incluyen en este diseño.  Los recursos de idioma para inglés y alemán se incluyen para todas estas cargas de trabajo. El diseño se actualiza a la última versión disponible.

```cmd
vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --lang de-DE
```

Si quiere actualizar un diseño existente en un diseño completo, use la opción --all, como se muestra en el ejemplo siguiente.

```cmd
vs_enterprise.exe --layout c:\VSLayout --all
```

## <a name="deploy-from-a-network-installation"></a>Implementación de una instalación de red

Los administradores pueden implementar Visual Studio en estaciones de trabajo cliente como parte de un script de instalación. O bien, los usuarios que tienen derechos de administrador pueden ejecutar la instalación directamente desde el recurso compartido para instalar Visual Studio en sus máquinas.

* Para realizar la instalación, los usuarios pueden ejecutar el comando siguiente: <br>
    ```cmd
    \\server\products\VS\vs_enterprise.exe
    ```

* Los administradores pueden realizar la instalación en modo desatendido con la ejecución del comando siguiente:
    ```cmd
    \server\products\VS\vs_enterprise.exe --quiet --wait --norestart
    ```

> [!IMPORTANT]
> Para evitar errores, asegúrese de que la ruta de acceso completa del diseño tenga menos de 80 caracteres.
>
> [!TIP]
> Cuando se ejecuta como parte de un archivo por lotes, la opción `--wait` garantiza que el proceso `vs_enterprise.exe` espere hasta que la instalación haya finalizado antes de devolver un código de salida.
>
> Resulta muy útil si un administrador de empresa quiere realizar más acciones en una instalación completada (por ejemplo, para [aplicar una clave de producto a una instalación correcta](automatically-apply-product-keys-when-deploying-visual-studio.md)), pero debe esperar a que la instalación finalice para controlar el código de retorno desde esa instalación.
>
> Si no usa `--wait`, el proceso `vs_enterprise.exe` se cierra antes de que la instalación se complete y devuelve un código de salida incorrecto que no representa el estado de la operación de instalación.

Cuando realice la instalación desde un diseño, el contenido que está instalado se adquirirá del diseño. Sin embargo, si selecciona un componente que no está en el diseño, se obtendrá de Internet.  Si quiere evitar que la instalación de Visual Studio descargue cualquier contenido que no esté en su diseño, use la opción `--noWeb`. Si se usa `--noWeb` y al diseño le falta cualquier contenido seleccionado que se va a instalar, se produce un error en la instalación.

> [!IMPORTANT]
> La opción `--noWeb` no impide que la configuración de Visual Studio busque actualizaciones. Para más información, consulte la página [Control de actualizaciones a implementaciones de Visual Studio basadas en red](controlling-updates-to-visual-studio-deployments.md).

### <a name="error-codes"></a>Códigos de error

Si ha usado el parámetro `--wait`, la variable de entorno `%ERRORLEVEL%` se establece en uno de los siguientes valores, según el resultado de la operación:

  | **Valor** | **Resultado** |
  | --------- | ---------- |
  | 0 | Operación completada correctamente |
  | 3010 | Operación completada correctamente, pero la instalación requiere reiniciar el equipo para que se pueda usar |
  | Otros | Condición de error: consulte los registros para obtener más información |

## <a name="update-a-network-install-layout"></a>Actualización de un diseño de instalación de red

A medida que estén disponibles actualizaciones de productos, puede que quiera [actualizar el diseño de instalación de red](update-a-network-installation-of-visual-studio.md) para incorporar paquetes actualizados.

## <a name="how-to-create-a-layout-for-a-previous-visual-studio-release"></a>Creación de un diseño para una versión anterior de Visual Studio

::: moniker range="vs-2017"

> [!NOTE]
> Los programas previos de Visual Studio que están disponibles en [visualstudio.microsoft.com](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) permiten descargar e instalar la versión de Visual Studio más reciente disponible cada vez que se ejecutan.
> 
> Por tanto, si descarga hoy un *programa previo* de Visual Studio y lo ejecuta de aquí a seis meses, se instalará la versión de Visual Studio que esté disponible en el momento que ejecute el programa previo.
> 
> Pero, si crea un *diseño* y lo instala a partir de él, el diseño instala la versión específica de Visual Studio que existe en el diseño. Aunque es posible que exista una versión más reciente en línea, obtiene la versión de Visual Studio que está en el diseño.

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> Los programas previos de Visual Studio que están disponibles en [visualstudio.microsoft.com](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) permiten descargar e instalar la versión de Visual Studio más reciente disponible cada vez que se ejecutan.
> 
> Por tanto, si descarga hoy un *programa previo* de Visual Studio y lo ejecuta de aquí a seis meses, se instalará la versión de Visual Studio que esté disponible en el momento que ejecute el programa previo.
> 
> Pero, si crea un *diseño* y lo instala a partir de él, el diseño instala la versión específica de Visual Studio que existe en el diseño. Aunque es posible que exista una versión más reciente en línea, obtiene la versión de Visual Studio que está en el diseño.

::: moniker-end

Si necesita crear un diseño para una versión anterior de Visual Studio, vaya a [https://my.visualstudio.com](https://my.visualstudio.com) para descargar versiones "no editables" de los programas previos de Visual Studio.

### <a name="how-to-get-support-for-your-offline-installer"></a>Obtención de soporte técnico para el instalador sin conexión

Si experimenta un problema con la instalación sin conexión, queremos saberlo. La mejor manera para hacérnoslo saber es usar la herramienta [Notificar un problema](../ide/how-to-report-a-problem-with-visual-studio.md). Con esta herramienta puede enviarnos la telemetría y los registros que necesitamos para ayudarnos a diagnosticar y corregir el problema.

También dispone de la opción del [**chat en directo**](https://visualstudio.microsoft.com/vs/support/#talktous) de soporte técnico para problemas relacionados con la instalación (disponible solo en inglés).

Tenemos también otras opciones de soporte técnico disponibles. Para obtener un listado, vea nuestra página [Hable con nosotros](../ide/talk-to-us.md).

## <a name="see-also"></a>Vea también

* [Actualización de una instalación basada en red de Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Control de actualizaciones a implementaciones de Visual Studio basadas en red](controlling-updates-to-visual-studio-deployments.md)
* [Guía del administrador de Visual Studio](visual-studio-administrator-guide.md)
* [Usar parámetros de la línea de comandos para instalar Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Identificadores de cargas de trabajo y componentes de Visual Studio](workload-and-component-ids.md)
