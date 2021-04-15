---
title: Actualización de una instalación basada en red
description: Más información sobre cómo actualizar una instalación de Visual Studio basada en red con el comando --layout
ms.date: 04/06/2021
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 1AF69C0E-0AC9-451B-845D-AE4EDBCEA65C
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 0f6e13333b6cab86f6485ddc18516039c712455a
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/13/2021
ms.locfileid: "107295954"
---
# <a name="update-a-network-based-installation-of-visual-studio"></a>Actualización de una instalación basada en red de Visual Studio

Se puede actualizar un diseño de instalación de red de Visual Studio con las actualizaciones de producto más recientes, de manera que se puede usar tanto como punto de instalación de la actualización más reciente de Visual Studio como para mantener instalaciones que ya están implementadas en estaciones de trabajo cliente.

## <a name="how-to-update-a-network-layout"></a>Actualización de un diseño de red

> [!IMPORTANT]
> En estas instrucciones se da por hecho que ya se ha creado previamente un diseño de instalación de red. Para más información sobre cómo hacerlo, vea la página [Creación de una instalación de red de Visual Studio](create-a-network-installation-of-visual-studio.md).

Para actualizar el recurso compartido de instalación de red de forma que incluya las actualizaciones más recientes, ejecute el comando `--layout` para descargar paquetes actualizados de forma incremental.

Si ha seleccionado un diseño parcial al [crear el diseño de red](create-a-network-installation-of-visual-studio.md), esas opciones se guardan. Cualquier comando de diseño futuro usa las opciones anteriores además de las nuevas que especifique.

Si hospeda un diseño en un recurso compartido, debe actualizar una copia privada del diseño (por ejemplo, c:\VSLayout) y, después de descargar todo el contenido actualizado, copiarla en el recurso compartido (por ejemplo,\\server\products\VS). Si no lo hace, existe una mayor probabilidad de que los usuarios que ejecutan el programa de instalación mientras se actualiza el diseño no puedan obtener todo el contenido del diseño ya que todavía no está completamente actualizado.

Veamos unos cuantos ejemplos de cómo crear y actualizar un diseño:

* Primero, aquí se muestra un ejemplo de cómo crear un diseño con una carga de trabajo solo para inglés:

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US
  ```

* Aquí se muestra cómo actualizar el mismo diseño a una versión más reciente. No tiene que especificar ningún parámetro de línea de comandos adicional. Las opciones anteriores se han guardado y se usarán mediante cualquier comando de diseño posterior en esta carpeta de diseño.

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout
  ```

* Aquí se muestra cómo actualizar el diseño a una versión más reciente de forma desatendida. La operación de diseño ejecuta el proceso de instalación en una ventana de consola nueva. La ventana se mantiene abierta para que los usuarios puedan ver el resultado final y un resumen de los errores que pudieran haberse producido. Si va a realizar una operación de diseño en modo desatendido (por ejemplo, tiene un script que se ejecuta periódicamente para actualizar el diseño a la versión más reciente), use el parámetro `--passive` y el proceso cerrará automáticamente la ventana.

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout --passive
  ```

* Aquí se muestra cómo agregar una carga de trabajo adicional y un idioma localizado.  (Este comando agrega la carga de trabajo *Desarrollo de Azure*).  Ahora tanto el escritorio administrado como Azure se incluyen en este diseño.  Los recursos de idioma para inglés y alemán también se incluyen para estas cargas de trabajo.  Además, el diseño se actualiza a la última versión disponible.

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --lang de-DE
  ```

    > [!IMPORTANT]
    > Una operación de actualización no instala componentes opcionales recién agregados. Si necesita los componentes opcionales recién agregados, quite los componentes opcionales antiguos del [archivo de respuesta](automated-installation-with-response-file.md) `Layout.JSON` e incluya los componentes necesarios en la sección "agregar" de `Layout.JSON`. 
    >
    > **Solución alternativa**: Después de una actualización, ejecute una operación de modificación independiente para instalar los componentes que faltan.

* Por último, aquí se muestra cómo agregar una carga de trabajo adicional y un idioma localizado sin actualizar la versión. (Este comando agrega la carga de trabajo *Desarrollo de ASP.NET y web*).  Ahora se incluyen en el diseño las cargas de trabajo de escritorio administrado, de Azure y Desarrollo de ASP.NET y web. Los recursos de idioma para inglés, francés y alemán también se incluyen para todas estas cargas de trabajo.  En cambio, el diseño no se ha actualizado a la última versión disponible cuando se ha ejecutado este comando. Sigue correspondiendo a la versión existente.

  ```cmd
  vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.NetWeb --lang fr-FR --keepLayoutVersion
  ```

## <a name="deploy-an-update-to-client-machines"></a>Implementación de una actualización en máquinas cliente

En función de cómo esté configurado el entorno de red, una actualización puede ser implementada por un administrador de empresa o se puede iniciar desde una máquina cliente.

* Los usuarios pueden actualizar una instancia de Visual Studio que se instaló desde una carpeta de instalación sin conexión:
  * Ejecute el instalador de Visual Studio.
  * Después, haga clic en **Actualizar**.

::: moniker range="vs-2017"

* Los administradores pueden actualizar las implementaciones de cliente de Visual Studio sin interacción del usuario con dos comandos independientes:
  * En primer lugar, actualice el instalador de Visual Studio: <br>```vs_enterprise.exe --quiet --update```
  * Luego, actualice la propia aplicación de Visual Studio: <br>```vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" --quiet --wait --norestart```

::: moniker-end

::: moniker range="vs-2019"

* Los administradores pueden actualizar las implementaciones de cliente de Visual Studio sin interacción del usuario con dos comandos independientes:
  * En primer lugar, actualice el instalador de Visual Studio: <br>```vs_enterprise.exe --quiet --update```
  * Luego, actualice la propia aplicación de Visual Studio: <br>```vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" --quiet --wait --norestart```

::: moniker-end

> [!NOTE]
> Use el comando [vswhere.exe](tools-for-managing-visual-studio-instances.md) para identificar la ruta de instalación de una instancia existente de Visual Studio en una máquina cliente.
>
> [!TIP]
> Para más información sobre cómo controlar cuándo se presentan notificaciones de actualización a los usuarios, consulte [Control updates to network-based Visual Studio deployments](controlling-updates-to-visual-studio-deployments.md) (Control de actualizaciones a implementaciones de Visual Studio basadas en red).

## <a name="verify-a-layout"></a>Comprobación de un diseño

Use `--verify` para realizar la comprobación en la caché sin conexión proporcionada. Comprueba si los archivos de paquetes están disponibles o no son válidos. Al finalizar la comprobación, imprime la lista de los archivos que faltan y que no son válidos.

```cmd
vs_enterprise.exe --layout <layoutDir> --verify
```

vs_enterprise.exe puede invocarse dentro de layoutDir.

> [!NOTE]
> Algunos archivos de metadatos importantes que la opción `--verify` necesita deben estar en la caché de diseño sin conexión. Si faltan estos archivos de metadatos, "--verify" no puede ejecutarse y la instalación genera un error. Si experimenta este error, vuelva a crear un nuevo diseño sin conexión en una carpeta diferente (o en la misma carpeta de la caché sin conexión). Para hacer esto, ejecute el mismo comando de diseño que ha usado para crear el diseño sin conexión inicial. Por ejemplo: `vs_enterprise.exe --layout <layoutDir>`.

Microsoft publica actualizaciones de Visual Studio periódicamente, por lo que el diseño que cree puede que no pertenezca a la misma versión que el diseño inicial.

> [!NOTE]
> La comprobación solo funciona para la versión más reciente de una versión secundaria específica de Visual Studio. En cuanto se lance una nueva versión, no funcionará la comprobación de anteriores versiones de nivel de revisión de la misma versión secundaria.

## <a name="fix-a-layout"></a>Corrección de un diseño

Use `--fix` para realizar la misma comprobación que `--verify` y también intente corregir los problemas identificados. El proceso `--fix` necesita una conexión a Internet, por lo que asegúrese de que su máquina esté conectada a Internet antes de invocar `--fix`.

```cmd
vs_enterprise.exe --layout <layoutDir> --fix
```

vs_enterprise.exe puede invocarse dentro de layoutDir.

## <a name="remove-older-versions-from-a-layout"></a>Eliminación de versiones anteriores de un diseño

Después de realizar actualizaciones de diseño en una caché sin conexión, la carpeta de la caché de diseño puede tener algunos paquetes obsoletos que la última instalación de Visual Studio ya no necesita. Puede usar la opción `--clean` para quitar paquetes obsoletos de una carpeta de caché sin conexión.

Para hacerlo, necesitará la ruta de acceso de archivo de los manifiestos de catálogo que contenga esos paquetes obsoletos. Puede encontrar los manifiestos de catálogo en la carpeta "Archivo", en la caché de diseño sin conexión. Cuando actualiza un diseño, se guardan ahí. En la carpeta "Archivo", existen una o más carpetas denominadas "GUID", cada una de las cuales contiene un manifiesto de catálogo obsoleto. El número de carpetas "GUID" debe ser el mismo que el número de actualizaciones realizadas en su caché sin conexión.

Algunos archivos se guardan dentro de cada carpeta "GUID". Los dos archivos de mayor interés son un archivo "catalog.json" y un archivo "version.txt". El archivo "catalog.json" es el manifiesto de catálogo obsoleto que necesitará pasar a la opción `--clean`. El otro archivo version.txt contiene la versión de este manifiesto de catálogo obsoleto. Basándose en el número de versión, puede decidir si quiere quitar paquetes obsoletos de este manifiesto de catálogo. Puede hacer lo mismo a medida que recorra las demás carpetas "GUID". Tras decidir los catálogos que quiera limpiar, ejecute el comando `--clean` proporcionando las rutas de acceso de archivos a estos catálogos.

Aquí se muestran algunos ejemplos de cómo usar la opción --clean:

```cmd
vs_enterprise.exe --layout <layoutDir> --clean <file-path-of-catalog1> <file-path-of-catalog2> …
```

```cmd
vs_enterprise.exe --layout <layoutDir> --clean <file-path-of-catalog1> --clean <file-path-of-catalog2> …
```

vs_enterprise.exe también puede invocarse dentro de &lt;layoutDir&gt;. Por ejemplo:

```cmd
c:\VSLayout\vs_enterprise.exe --layout c:\VSLayout --clean c:\VSLayout\Archive\1cd70189-fc55-4583-8ad8-a2711e928325\Catalog.json --clean c:\VS2017Layout\Archive\d420889f-6aad-4ba4-99e4-ed7833795a10\Catalog.json
```

Cuando ejecuta este comando, la instalación analiza la carpeta de caché sin conexión para buscar la lista de archivos que quitará. Después, tendrá la oportunidad de revisar los archivos que van a eliminarse y confirmar su eliminación.

## <a name="get-support-for-your-offline-installer"></a>Obtención de soporte técnico para el instalador sin conexión

Si experimenta un problema con la instalación sin conexión, queremos saberlo. La mejor manera para hacérnoslo saber es usar la herramienta [Notificar un problema](../ide/how-to-report-a-problem-with-visual-studio.md). Con esta herramienta puede enviarnos la telemetría y los registros que necesitamos para ayudarnos a diagnosticar y corregir el problema.

También dispone de la opción del [**chat en directo**](https://visualstudio.microsoft.com/vs/support/#talktous) de soporte técnico para problemas relacionados con la instalación (disponible solo en inglés).

Tenemos también otras opciones de soporte técnico disponibles. Para obtener una lista, consulte nuestra página [Comentarios](../ide/feedback-options.md).

## <a name="see-also"></a>Vea también

* [Instalación de Visual Studio](install-visual-studio.md)
* [Guía del administrador de Visual Studio](visual-studio-administrator-guide.md)
* [Usar parámetros de la línea de comandos para instalar Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Herramientas para detectar y administrar instancias de Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Control updates to network-based Visual Studio deployments](controlling-updates-to-visual-studio-deployments.md) (Control de actualizaciones de implementaciones de Visual Studio basadas en red)
* [Ciclo de vida y mantenimiento del producto de Visual Studio](/visualstudio/releases/2019/servicing/)
